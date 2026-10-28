## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, conclusions) as provided
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and alignment with stated aims; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors propose that structure-based similarity searches using the experimentally validated Zα domain of human ADAR1 (PDB 3f21) can identify new Z-DNA/Z-RNA binding proteins. They report 14 candidate proteins from the PDB and 185 from AlphaFold2 models, and use molecular docking to support functional conservation of key residues.
- **Visible evidence base** Tables 1 and 2 (referenced), Figures 2-6 (referenced), Supplementary Materials S1-S4 (referenced but not provided), Methods section 3.1-3.6
- **Missing materials affecting confidence** Supplementary Materials S1-S4 (functional annotation lists, AlphaFold models, NLS predictions, docking poses) are referenced but not included; Table 1 and Table 2 contents are not fully reproduced in the provided text; specific numerical outputs from PDBeFold and RUPEE searches (Q-scores, TM-scores, RMSD values) are not itemized; docking scores for RPA2 and other candidates are not reported numerically

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach to identifying novel Z-DNA/Z-RNA binding proteins through structural similarity, which could have broad implications for understanding nucleic acid recognition. However, the evidence provided is largely computational and predictive, with no experimental validation. The core claims of "high functional conservation" and "suggesting that Z-DNA/Z-RNA recognition may play an important role" are not fully supported by the data presented, as docking alone does not establish functional binding. The manuscript would benefit from clearer presentation of search parameters, more rigorous statistical thresholds, and explicit acknowledgment of the limitations of computational predictions.
- **Who would be interested in the results, and why** Researchers studying non-B DNA structures, Z-DNA/Z-RNA biology, nucleic acid-protein interactions, and structural bioinformatics. The identification of new candidate proteins could inform experimental studies in innate immunity, viral pathogenesis, and genome stability. The methodological approach may also interest computational biologists developing structure-based function prediction tools.
- **Major strengths** The study addresses an important gap in the field, as only a small number of Zα domain-containing proteins are known. The use of both experimentally determined structures (PDB) and predicted models (AlphaFold2) is a comprehensive approach. The inclusion of molecular docking to assess potential nucleic acid binding is a reasonable first step. The authors appropriately acknowledge the limitations of AlphaFold2 predictions and restrict their main conclusions to experimentally resolved structures.
- **Major Concerns** The central claim of identifying "new Z-DNA/Z-RNA binding proteins" is based solely on structural similarity and docking, without any experimental validation. The threshold choices (Q-score > 0.55, TM-score > 0.6) are presented as "stringent" but lack statistical justification or comparison to known false-positive rates. The docking analysis for RPA2 is described qualitatively, with no quantitative scores or comparison to known Zα-Z-DNA complexes. The functional significance of the identified proteins is speculative, and the connection to disease (e.g., viral infection) is not experimentally tested.
- **Minor Comments** The manuscript would benefit from a clearer definition of the "Zα domain" in terms of structural boundaries, as the authors note ambiguity in the current Pfam definition. The statement about "convergent evolution" is plausible but not rigorously tested. The NLS prediction analysis is mentioned but not described in sufficient detail. The authors should clarify whether the 185 AlphaFold2 hits were filtered by any functional criteria beyond structural similarity.
- **Technical failings that need to be addressed before the case is established** The lack of experimental validation for any of the 14 candidate proteins is a critical gap. The docking results are not quantitatively compared to known Zα-Z-DNA/Z-RNA complexes, which would provide a benchmark for specificity. The statistical significance of the structural similarity scores is not established. The manuscript does not provide a clear negative control to demonstrate that the search method does not produce false positives at the chosen thresholds.
- **Assessment against Nature-style criteria** Originality: Moderate. The approach is not entirely novel, as structural similarity searches are standard, but the application to Zα domain discovery is relatively underexplored. Scientific importance: Moderate. If validated, the findings could expand the known repertoire of Z-DNA/Z-RNA binding proteins, but the current evidence is too preliminary to establish significance. Interdisciplinary readership: Limited. The manuscript is primarily of interest to structural biologists and nucleic acid researchers, with less appeal to a broader audience. Technical soundness: Weak. The computational methods are appropriate but the lack of experimental validation and quantitative benchmarking undermines the conclusions. Readability for nonspecialists: Adequate. The manuscript is generally clear, though some sections assume familiarity with structural biology terminology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a reasonable computational screen but does not provide sufficient evidence to support the claim that the identified proteins are bona fide Z-DNA/Z-RNA binding proteins. Experimental validation or at minimum a more rigorous computational benchmark would be required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence mismatch
- **Claim pointer** "A structure-based similarity search found 14 proteins with highly similar Zα domain structure in experimentally-defined proteins and 185 proteins with a putative Zα domain using the AlphaFold2 models."
- **Evidence pointer** Table 2, Figure 2, Section 2.1
- **Concern** The claim of "highly similar" is based on Q-scores above 0.55, but the manuscript does not provide the actual Q-scores, RMSD values, or alignment lengths for the 14 hits. Without these data, the reader cannot assess whether the similarity is indeed high or merely above an arbitrary threshold. Furthermore, the choice of 0.55 is not justified with reference to known distributions of Q-scores for unrelated proteins.
- **Why it matters** The entire premise of the manuscript rests on the validity of the structural similarity search. If the threshold is too permissive, the 14 candidates may include false positives, undermining the claim that they are genuine Zα domain homologs.
- **Resolution test** Provide a supplementary table listing all 14 hits with their Q-scores, RMSD values, alignment lengths, and PDB identifiers. Include a statistical analysis showing that the Q-score distribution for the hits is significantly different from that of a random set of proteins. Alternatively, demonstrate that known Zα domains score above the threshold while a set of negative controls (e.g., proteins with similar folds but no Z-DNA binding) score below.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Overinterpretation of computational results
- **Claim pointer** "Structure-based alignment and molecular docking confirmed high functional conservation of amino acids involved in Z-DNA/Z-RNA, suggesting that Z-DNA/Z-RNA recognition may play an important role in a variety of cellular processes."
- **Evidence pointer** Section 2.3, Figure 5, Supplementary Material S4
- **Concern** The docking analysis is presented as "confirming" functional conservation, but docking scores alone do not demonstrate binding affinity or specificity. The manuscript does not report the HDOCK scores for the RPA2-Z-DNA/Z-RNA complexes, nor does it compare these scores to those of known Zα domain complexes or to negative controls (e.g., docking a non-Z-DNA binding protein to Z-DNA). The statement that "inspection of the best docking poses revealed that it in general follows the rules described above" is vague and not supported by quantitative data.
- **Why it matters** Molecular docking is a predictive tool with well-known limitations, including false positives and sensitivity to input structures. Without benchmarking against known complexes and reporting quantitative scores, the claim of "high functional conservation" is not substantiated.
- **Resolution test** Report the HDOCK scores for all 14 candidates and compare them to scores obtained for known Zα-Z-DNA/Z-RNA complexes and for a set of negative control proteins. Provide a statistical analysis (e.g., a receiver operating characteristic curve) to demonstrate that the docking scores can discriminate between known binders and non-binders. If possible, include a figure showing the predicted binding interfaces and their conservation across the candidates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Lack of experimental validation
- **Claim pointer** "This paper aimed to search for new Z-DNA/Z-RNA binding proteins" and "suggesting that Z-DNA/Z-RNA recognition may play an important role in a variety of cellular processes."
- **Evidence pointer** Sections 2.1-2.4, Conclusions
- **Concern** The manuscript identifies 14 candidate proteins but provides no experimental evidence that any of them actually bind Z-DNA or Z-RNA. The authors acknowledge this limitation in the conclusions ("Further experimental validation is required"), but the abstract and results sections present the findings as if the proteins are "Z-DNA/Z-RNA binding proteins" without qualification. This overstatement is problematic, as structural similarity does not guarantee function.
- **Why it matters** The central claim of the manuscript is that new Z-DNA/Z-RNA binding proteins have been identified. Without experimental validation (e.g., electrophoretic mobility shift assays, circular dichroism, or cellular assays), the claim is not established. The manuscript's conclusions go beyond what the evidence supports.
- **Resolution test** Add a clear statement in the abstract and results that these are "candidate" proteins requiring experimental validation. If possible, include at least one experimental validation (e.g., in vitro binding assay for one or two of the most promising candidates) to strengthen the claim. Alternatively, reframe the manuscript as a computational prediction study and temper the conclusions accordingly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Incomplete reporting of methods and results
- **Claim pointer** "A total of 185 unique proteins were selected after inspection, among which 59 proteins currently do not have complete functional annotation."
- **Evidence pointer** Section 2.1, Supplementary Material S1
- **Concern** The selection of 185 proteins from the initial 308 returned by RUPEE is described as involving "manual inspection of the alignments," but the criteria for this inspection are not specified. The manuscript does not state how many proteins were excluded and for what reasons, nor does it provide a list of the 185 proteins or their predicted Zα domain boundaries. The functional annotation categories (e.g., "transcriptional regulators") are mentioned but not quantified.
- **Why it matters** The reproducibility of the study depends on a clear description of the filtering process. Without this, the reader cannot assess whether the selection was biased or whether the 185 proteins are representative of the initial hits.
- **Resolution test** Provide a detailed description of the manual inspection criteria (e.g., presence of basic residues, structural accessibility, absence of large disordered regions). Include a supplementary table listing all 185 proteins with their UniProt identifiers, predicted Zα domain boundaries, and functional annotations. Quantify the number of proteins in each functional category.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Section 2.1, definition of "Zα domain"
- **Evidence pointer** Section 2.1, Pfam ID PF02295
- **Issue** The authors express skepticism about the current Pfam definition of the Zα domain but continue to use the term without providing an alternative definition. This creates ambiguity about what structural features are being searched for.
- **Required correction** Define the structural criteria used to identify a "Zα-like" fold (e.g., specific secondary structure arrangement, residue conservation, electrostatic properties) and state whether these criteria differ from the Pfam definition.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Presentation of docking results
- **Affected element** Section 2.3, Figure 5
- **Evidence pointer** Section 2.3, Figure 5
- **Issue** The docking results for RPA2 are described qualitatively, with no mention of the HDOCK score or the ranking of the best model. The figure is referenced but not described in detail.
- **Required correction** Report the HDOCK score for the best RPA2-Z-DNA and RPA2-Z-RNA models, and state the number of models generated. Briefly describe the predicted binding interface and how it compares to known Zα domain interactions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Overstatement in abstract
- **Affected element** Abstract, last sentence
- **Evidence pointer** Abstract
- **Issue** The abstract states that the results "suggest that Z-DNA/Z-RNA recognition may play an important role in a variety of cellular processes," which is a broad claim not directly supported by the data, as the functional significance of the identified proteins is not experimentally tested.
- **Required correction** Soften the claim to "suggest that Z-DNA/Z-RNA recognition may be more widespread than previously thought, warranting further experimental investigation."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Missing statistical context
- **Affected element** Section 2.1, Q-score threshold
- **Evidence pointer** Section 2.1, Table 2
- **Issue** The choice of Q-score threshold 0.55 is stated as "stringent," but no statistical context is provided (e.g., distribution of Q-scores for random protein pairs).
- **Required correction** Provide a brief justification for the threshold, such as a reference to previous studies using PDBeFold or an analysis of Q-score distributions for known Zα domains versus unrelated proteins.

## Risk / unsupported claims
- The claim that 14 proteins are "new Z-DNA/Z-RNA binding proteins" is unsupported without experimental validation; they should be described as "candidates."
- The claim of "high functional conservation" based on docking is unsupported without quantitative benchmarking against known complexes and negative controls.
- The claim that "Z-DNA/Z-RNA recognition may play an important role in a variety of cellular processes" is speculative and not directly tested.
- The functional significance of the identified proteins in innate immunity and viral infection is inferred from literature but not experimentally demonstrated.
- The reliability of the 185 AlphaFold2-based predictions is acknowledged as limited, but the manuscript does not provide a clear framework for prioritizing these candidates for future validation.