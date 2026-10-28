## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided
- **Assessment boundary** Scientific validity, methodological soundness, evidence quality, and clarity of claims as presented in the provided text
- **Shared manuscript claim summary** The authors present FiveFold, a single-sequence method for predicting conformational ensembles of proteins. The method uses a protein folding shape code (PFSC) of 27 letters to describe local folds of five amino acid residues, constructs a protein folding variation matrix (PFVM) from a query sequence, generates multiple PFSC strings by combining letters across columns, and builds 3D structures by screening a PDB-derived database for conformationally homologous fragments. The authors claim the method can predict multiple conformations, capture intrinsic disorder, and distinguish structural effects of single-residue mutations.
- **Visible evidence base** Text descriptions of methods and results; references to Tables 1-6 and Figures 1-8; no actual data values, structural coordinates, or quantitative performance metrics are provided in the supplied text
- **Missing materials affecting confidence** All figures and tables are referenced but not provided; no quantitative accuracy metrics (e.g., RMSD, TM-score, pLDDT comparisons); no benchmark details beyond protein names; no statistical analysis; no comparison with existing ensemble prediction methods; no code or web server access details

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely problem: moving beyond single-structure prediction to conformational ensembles. The conceptual framework of using a discrete shape code to enumerate local folding possibilities is interesting and potentially useful. However, the manuscript as provided does not establish the validity of the method. The results section is largely qualitative, with no quantitative metrics, no statistical comparisons, and no clear demonstration that predicted ensembles are biologically meaningful or structurally accurate. The claims of accuracy, flexibility, and mutation sensitivity are not supported by the evidence presented. The writing contains numerous grammatical errors and unclear passages that impede comprehension. The manuscript is not currently suitable for publication in its present form.

- **Who would be interested in the results, and why** Structural biologists, computational biologists, and researchers studying intrinsically disordered proteins would be interested in a method that can generate conformational ensembles from sequence alone. If validated, such a method could complement AlphaFold by providing multiple states rather than a single prediction. Researchers studying protein mutations and their structural consequences might also find value. However, interest will depend critically on demonstrated quantitative performance, which is currently absent.

- **Major Strengths**
  1. The problem addressed is significant: conformational ensembles are biologically relevant and not provided by current state-of-the-art methods like AlphaFold.
  2. The conceptual approach of using a discrete shape code (PFSC) to discretize conformational space is creative and potentially scalable.
  3. The method is designed as a single-sequence approach, avoiding dependence on MSA, which is a genuine advantage for orphan sequences and mutation studies.
  4. The authors address the Levinthal paradox explicitly and propose a practical enumeration strategy, which is conceptually valuable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that FiveFold predicts protein structures "with accuracy" and that predicted ensembles "cover wider range of flexible conformational space than given structures."
- **Evidence pointer** Results section, Figures 3-5, Tables 2-5; location not provided
- **Concern** No quantitative accuracy metrics are reported. The text mentions "overlay similarity scores" and "PFSA scores" but provides no numerical values, no thresholds for acceptance beyond a single mention of 0.70 for PFSA, and no comparison against experimental structures or AlphaFold predictions in quantitative terms. The claim that predicted structures "well match" given structures is subjective and unsupported.
- **Why it matters** Without quantitative validation, the reader cannot assess whether the method produces structures of any useful accuracy. The central claim of the paper depends on demonstrating that predicted ensembles are structurally meaningful.
- **Resolution test** Provide quantitative metrics for each predicted structure compared to experimental references, including RMSD, TM-score, or equivalent measures. Report distributions of scores across the ensemble, not just selected examples. Compare against AlphaFold predictions using the same metrics.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** The method constructs 3D structures by "high-throughput screening PDB-PFSC database with conformational homologous search" and accepts hits with PFSA score greater than 0.70.
- **Evidence pointer** Materials and methods, "Construction of ensemble of protein 3D structures"; location not provided
- **Concern** The description of how PFSC strings are converted into 3D structures is insufficiently detailed. How are fragments of 40-50 residues assembled? How are overlaps handled? How is the final structure optimized? What is the "conformational homologous search" algorithm? How is the PFSA score computed? The criteria for accepting a hit (PFSA > 0.70) is mentioned but no justification is given for this threshold.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without a detailed algorithmic description, other researchers cannot implement or evaluate the method independently.
- **Resolution test** Provide a complete algorithmic description, including pseudocode or a flow diagram, detailing each step from sequence to ensemble of 3D structures. Specify the search algorithm, scoring function, fragment assembly procedure, and any post-processing steps.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation rigor
- **Claim pointer** The authors state that "the results demonstrated an effective algorithm and biological meaningful process well to predict protein multiple conformation structures."
- **Evidence pointer** Abstract; Results sections for P53_HUMAN, LEF1_HUMAN, Q8GT36_SPIOL; location not provided
- **Concern** The validation is limited to three proteins, with no systematic benchmark. For P53_HUMAN, only the DNA-binding domain is discussed in detail. For LEF1_HUMAN, no experimental structures exist, so validation is only against AlphaFold. For Q8GT36_SPIOL, the comparison with NMR structures is qualitative. No metrics such as ensemble coverage, diversity, or agreement with experimental observables (e.g., chemical shifts, SAXS profiles) are provided.
- **Why it matters** A method for conformational ensembles must be validated against known ensembles, not just single structures. The current validation does not demonstrate that the predicted ensembles are biologically meaningful or that they capture the true conformational heterogeneity.
- **Resolution test** Validate on a benchmark set of proteins with known conformational ensembles (e.g., from NMR or MD simulations). Report quantitative measures of ensemble quality, such as overlap with experimental ensembles, coverage of known conformational states, and diversity relative to single-structure predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing methods
- **Claim pointer** The authors position FiveFold as overcoming limitations of AlphaFold, particularly regarding multiple conformations and intrinsic disorder.
- **Evidence pointer** Introduction; Discussion sections "Accuracy vs. flexibility" and "Deep learning vs. meaningful biophysical algorithm"; location not provided
- **Concern** No direct comparison with existing ensemble prediction methods is provided. The discussion mentions AlphaFold limitations but does not quantitatively compare FiveFold against AlphaFold or other methods (e.g., ESMFold, RoseTTAFold, or dedicated disorder predictors like IUPred or PONDR) on the same proteins.
- **Why it matters** To establish the value of FiveFold, the authors must demonstrate that it provides information not available from existing methods, ideally with quantitative comparisons on the same test cases.
- **Resolution test** Run AlphaFold and at least one other ensemble or disorder prediction method on the same benchmark proteins. Report comparative metrics for accuracy, ensemble diversity, and disorder prediction quality.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors claim that PFVM can reveal structural differences caused by single-residue mutations, using hemoglobin mutations E7V and E27K as examples.
- **Evidence pointer** Discussion section "MSA vs. single sequence method", Table 6; location not provided
- **Concern** The mutation analysis is presented qualitatively. The text states that E27K "deformed" the helix and changed side chain orientation, but no quantitative comparison of the predicted structures before and after mutation is provided. The biological significance of the observed changes is not discussed.
- **Why it matters** The claim that FiveFold can distinguish mutation effects is potentially valuable for clinical and pharmaceutical applications, but it requires quantitative demonstration that predicted structural changes are meaningful and not artifacts of the method.
- **Resolution test** Provide quantitative structural comparison (e.g., local RMSD, dihedral angle changes) between wild-type and mutant predictions. Discuss whether the predicted changes are consistent with known functional effects of these mutations.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract contains grammatical errors and unclear phrasing, e.g., "which is actually involving to the solution" and "token as the benchmark."
- **Required correction** Rewrite the abstract for clarity and grammatical correctness. For example, "which relates to the protein folding problem and the study of intrinsically disordered proteins" and "used as benchmarks."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Methods, PFSC definition
- **Evidence pointer** Materials and methods, "PFSC" section; location not provided
- **Issue** The text states "27 letters inculding '$' as PFSC" but does not explain what the "$" symbol represents or why it is included. The relationship between the 27 letters and the 20 amino acids is unclear.
- **Required correction** Clarify the PFSC alphabet, explain the meaning of each symbol, and describe how the 27 letters map to the conformational space of five residues.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, P53_HUMAN section
- **Evidence pointer** Results, "P53_HUMAN" section; location not provided
- **Issue** The text mentions "12 of P53 DNA-binding domain structures plus AlphaFold prediction" in Table 1, but the selection criteria for these 12 structures are not stated.
- **Required correction** State the criteria for selecting the 12 structures and whether they represent the full diversity of available P53 structures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results, Q8GT36_SPIOL section
- **Evidence pointer** Results, "Q8GT36_SPIOL" section; location not provided
- **Issue** The text states that 10 conformational 3D structures were predicted, but Table 5 lists 22 PFSC strings in section C. The relationship between the 22 strings and the 10 structures is unclear.
- **Required correction** Clarify how many structures were actually constructed and why only 10 are shown in Figure 8.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Methods, software availability
- **Evidence pointer** Materials and methods; location not provided
- **Issue** The text mentions that "the software, web server and supporting database are already established" but provides no URLs, access instructions, or availability statement.
- **Required correction** Provide a Data Availability statement with URLs or access instructions for the software, web server, and database.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language quality
- **Affected element** Entire manuscript
- **Evidence pointer** Throughout; location not provided
- **Issue** The manuscript contains numerous grammatical errors, awkward phrasings, and typographical issues (e.g., "inculding," "Finger 3" instead of "Figure 3," "interesting in" instead of "interested in").
- **Required correction** The manuscript requires thorough language editing by a native English speaker or professional editing service.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Introduction
- **Evidence pointer** Introduction; location not provided
- **Issue** The introduction references limitations of AlphaFold but does not cite specific papers that discuss these limitations in detail.
- **Required correction** Add appropriate citations for AlphaFold limitations and for existing ensemble prediction methods.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 2-5, 7-8
- **Evidence pointer** Figures 2-5, 7-8; location not provided
- **Issue** The figure captions describe what is shown but provide no quantitative information. Without the actual figures, the reader cannot assess the quality of structural superposition or the degree of conformational diversity.
- **Required correction** Ensure figures include clear labels, color scales, and quantitative annotations where relevant. Consider adding a figure showing the distribution of ensemble members with quantitative diversity metrics.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results sections; location not provided
- **Issue** No statistical analysis is presented. It is unclear whether differences between predicted and experimental structures are within expected error ranges.
- **Required correction** Add appropriate statistical measures, such as mean and standard deviation of accuracy metrics across the ensemble, and significance tests where relevant.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Scope
- **Affected element** Discussion, Future development
- **Evidence pointer** Discussion, "Future development" section; location not provided
- **Issue** The future development section is speculative and does not address current limitations of the method, such as the quality of the PDB-derived database or potential biases in fragment selection.
- **Required correction** Add a balanced discussion of current limitations and how they might be addressed.

## Risk / unsupported claims
1. The claim that FiveFold "provided an effective algorithm and biological meaningful process well to predict protein multiple conformation structures" is unsupported by quantitative evidence in the provided text.
2. The claim that predicted ensembles "cover wider range of flexible conformational space than given structures" is not demonstrated with any diversity or coverage metrics.
3. The claim that FiveFold can "distinguish the structure difference caused by individual residue replacement" is based on a single qualitative example (hemoglobin mutations) with no quantitative comparison.
4. The claim that the method provides "a meaningful biophysical algorithm" is asserted but not substantiated with mechanistic detail or comparison against physics-based methods.
5. The claim that the method "can predict the multiple conformational structures in flexibility, but also can predict structure in accuracy" is not supported by any accuracy metrics.
6. The statement that "the PFVM contains all necessary PFSC letters which is able to form the PFSC strings matching exact conformations for all given structures" is a strong claim that requires systematic demonstration across many proteins, not just the examples shown.
7. The computational efficiency claims ("takes about 20 min", "takes about 5 min") are anecdotal and not benchmarked systematically.

## Assessment against Nature-style criteria
- **Originality**: The concept of using a discrete shape code to enumerate conformational possibilities is creative and distinct from existing deep learning approaches. However, the originality is diminished by the lack of clear novelty in the final structure construction step, which appears to rely on database screening similar to existing fragment assembly methods.
- **Scientific importance**: The problem of conformational ensembles is important and timely. If the method were validated, it could have broad impact. However, the current evidence does not establish that the method achieves its goals, so the importance remains potential rather than demonstrated.
- **Interdisciplinary readership**: The topic bridges structural biology, computational biology, and AI. The manuscript could appeal to these communities, but the poor writing quality and lack of quantitative results will limit its accessibility and impact.
- **Technical soundness**: The technical soundness cannot be assessed from the provided text. The methods are described at a high level without algorithmic detail, and no quantitative validation is presented. The validation strategy is inadequate for the claims made.
- **Readability for nonspecialists**: The manuscript is not readable in its current form due to grammatical errors, unclear phrasing, and undefined terminology. A nonspecialist would struggle to understand the method or its significance.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an important problem and presents a conceptually interesting approach, but the evidence provided is insufficient to support the central claims. The lack of quantitative validation, incomplete methodological detail, and poor writing quality are major barriers. The authors should be encouraged to resubmit a revised manuscript with rigorous quantitative benchmarking, complete algorithmic descriptions, and professional language editing.