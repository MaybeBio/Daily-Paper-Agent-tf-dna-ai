## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the reported peptide design strategy and experimental characterization
- **Shared manuscript claim summary** The authors report the rational design of peptide inhibitors targeting the KIX-MLL interaction using Rosetta-based saturation mutagenesis combined with helical propensity prediction. They identify a T2857W mutant of the MLL TAD peptide with approximately twofold higher binding affinity for KIX than the wild-type peptide and demonstrate its inhibitory activity in competitive binding assays.
- **Visible evidence base** Computational predictions (Rosetta dG_separated scores, AGADIR helical propensity), CD spectroscopy, ITC binding measurements, SPR-based competitive inhibition assays, fluorescence polarization assays
- **Missing materials affecting confidence** Supplementary figures referenced but not provided in the submitted material; raw sensorgrams and titration curves not available for independent assessment; no structural validation data (e.g., NMR or X-ray) for the designed mutant complexes

## Reviewer
- **Overall assessment** The manuscript presents a straightforward application of established computational protein design tools to a well-characterized protein-protein interaction system. The experimental work is competently executed and the primary claim, that a T2857W mutation in the MLL TAD peptide enhances KIX binding approximately twofold, is supported by the ITC data. However, the study represents an incremental advance over existing peptide inhibitors of the KIX-MLL interaction, and the authors' assertion that this peptide has the highest affinity among all previously reported inhibitors targeting the MLL site requires more careful benchmarking against the literature. The disconnect between computational predictions and experimental outcomes, acknowledged by the authors, raises questions about the general utility of the design approach as presented.
- **Who would be interested in the results, and why** Researchers in the fields of peptide therapeutics, protein-protein interaction inhibition, and transcriptional regulation. The work may also be of interest to practitioners of computational protein design who seek examples of Rosetta-based design applied to intrinsically disordered peptide binding motifs. The KIX domain is a well-studied model system for understanding multi-domain transcriptional coactivator interactions, so the broader transcriptional regulation community may find the affinity data useful as reference points.
- **Major strengths** The study addresses a biologically relevant target with clear disease associations. The experimental characterization is thorough, employing multiple orthogonal biophysical methods (ITC, SPR, CD, fluorescence polarization). The authors are appropriately cautious in interpreting the limited correlation between Rosetta scores and experimental binding data. The comparison of single and double mutants provides useful information about the non-additivity of beneficial mutations in this system.
- **Major Concerns** The central claim of achieving the highest affinity KIX inhibitor targeting the MLL site requires more rigorous comparison with previously reported peptides, including those with non-natural amino acids and stapled peptides. The computational design pipeline produced 24 candidates, of which only 3 showed improved binding, and the best mutant was not the top-ranked by Rosetta, suggesting the predictive power of the approach is limited. The functional significance of a twofold affinity improvement is not established, particularly in the context of cellular assays or competitive displacement of full-length MLL. The specificity of the designed peptide for the MLL site over the c-Myb site is only indirectly addressed.
- **Minor Comments** The authors should clarify why the Kd values differ between ITC and SPR measurements for the same interaction. The fluorescence polarization competitive assay uses FITC-MLL, but the Kd for FITC-MLL binding to KIX differs from the unlabeled peptide; this discrepancy should be discussed. The statement that the approach "may be useful" for developing peptide inhibitors is vague and should be supported by a more concrete assessment of the method's success rate and limitations.
- **Technical failings that need to be addressed before the case is established** The lack of direct comparison with previously reported high-affinity KIX-MLL inhibitors in the same assay conditions; the absence of any cellular or functional assay demonstrating biological activity of the designed peptide; the unvalidated assumption that the T2857W mutation enhances binding through hydrophobic burial without structural evidence.
- **Assessment against Nature-style criteria** Originality: The application of Rosetta saturation mutagenesis to the KIX-MLL interaction is not conceptually novel, though the specific system and mutations are new. Scientific importance: The KIX-MLL interaction is a valid therapeutic target, but a twofold affinity improvement over the wild-type peptide is modest and unlikely to change the field's understanding or therapeutic approaches. Interdisciplinary readership: The work bridges computational protein design and biophysical characterization, which may attract readers from both communities, but the narrow scope limits broader appeal. Technical soundness: The experimental methods are appropriate and well-executed, though the computational-experimental correlation is weak. Readability for nonspecialists: The manuscript is clearly written and accessible, with appropriate context provided for the biological system.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding benchmarking against existing inhibitors and demonstration of functional relevance.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim of highest affinity among reported KIX-MLL inhibitors
- **Claim pointer** "To our knowledge, this peptide has the highest affinity for KIX among all previously reported inhibitors that target the MLL site of KIX."
- **Evidence pointer** Discussion section, location not provided
- **Concern** The authors claim their T2857W peptide has the highest affinity for KIX among all previously reported inhibitors targeting the MLL site. However, the comparison with prior work is superficial. The Discussion mentions stapled peptides and non-natural amino acid-containing peptides only in passing, without providing a quantitative comparison of their reported Kd or IC50 values. The claim requires a systematic literature comparison with binding affinities measured under comparable conditions.
- **Why it matters** This claim is a central element of the paper's significance. If prior inhibitors with higher affinity exist, the novelty and impact of the work are substantially diminished. The claim as stated cannot be verified from the provided material.
- **Resolution test** Provide a comprehensive table comparing the Kd and IC50 values of all previously reported KIX-MLL inhibitors with the T2857W peptide, with clear specification of assay conditions for each entry. If prior inhibitors have comparable or better affinity, revise the claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance of twofold affinity improvement
- **Claim pointer** "We demonstrated that the T2857W mutant of the MLL TAD peptide has a ~twofold higher affinity for KIX than the wild-type MLL and is effective in inhibiting the KIX-MLL interaction."
- **Evidence pointer** Results sections "KIX-binding affinity of designed peptides" and "Competitive inhibition assay", location not provided
- **Concern** The manuscript demonstrates a modest approximately twofold improvement in binding affinity and inhibitory activity. However, no experiments address whether this improvement translates into meaningful biological or therapeutic benefit. The wild-type MLL TAD peptide already binds KIX with micromolar affinity, and the twofold improvement may not be sufficient to achieve effective inhibition in a cellular context where competing interactions and high local concentrations of natural binding partners exist.
- **Why it matters** The stated goal of the work is to develop inhibitors with potential therapeutic applications. Without evidence that the improved affinity translates into functional inhibition in a relevant biological context, the practical significance of the design is unclear.
- **Resolution test** Perform cellular or in vitro transcription assays demonstrating that the T2857W peptide can disrupt KIX-MLL-dependent transcriptional activation. Alternatively, clearly frame the work as a proof-of-concept for the design approach rather than a therapeutic lead, and temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Limited predictive power of computational design
- **Claim pointer** "We performed theoretical saturation mutagenesis using the Rosetta software to search for mutants expected to bind KIX more tightly than the wild-type MLL TAD."
- **Evidence pointer** Results section "Computational design using Rosetta", Figure 2, location not provided
- **Concern** Of the 24 mutants selected based on Rosetta predictions, only 3 showed experimentally improved binding affinity, and the best performer (T2857W) was not the top-ranked by Rosetta. The authors acknowledge the low correlation between Rosetta scores and experimental results (r = 0.42-0.47), but the manuscript does not critically evaluate what this means for the utility of the design approach. The selection funnel from 558 computationally screened mutants to 24 candidates to 3 hits represents a success rate that should be discussed in the context of alternative approaches.
- **Why it matters** The authors suggest their approach "may be useful for rationally developing helical peptides." The data presented show that the computational predictions are weakly predictive, and the manuscript would benefit from a more honest assessment of the method's limitations and potential improvements.
- **Resolution test** Provide a more detailed analysis of the relationship between computational predictions and experimental outcomes, including discussion of why certain predictions failed. Consider whether additional filters (e.g., structural analysis, molecular dynamics) could improve the selection process.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Discrepancy between ITC and SPR Kd values
- **Affected element** Results section "KIX-binding affinity of designed peptides" and "Competitive inhibition assay"
- **Evidence pointer** Figure 4c,d and Figure 5a,b, location not provided
- **Issue** The Kd for the wild-type MLL TAD binding to KIX is reported as 2.02 ± 0.04 μM by ITC but 4.94 ± 0.02 μM by SPR. This approximately 2.5-fold discrepancy is not discussed. Possible explanations include differences in immobilization effects, buffer conditions, or fitting models.
- **Required correction** Add a brief discussion of the discrepancy and its potential sources, or provide a rationale for why the two methods yield different values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** FITC labeling effects on binding affinity
- **Affected element** Results section "Competitive inhibition assay using fluorescence polarization"
- **Evidence pointer** Figure 6a, location not provided
- **Issue** The Kd for FITC-MLL binding to KIX measured by fluorescence polarization is 1.13 ± 0.01 μM, which differs from both the ITC and SPR values for the unlabeled peptide. The authors attribute this to the FITC label but do not explore whether the label affects the binding mode or the inhibitory activity of the peptide in the competition assay.
- **Required correction** Discuss the potential impact of FITC labeling on the peptide's binding properties and whether the IC50 values obtained from the fluorescence polarization competition assay are directly comparable to those from SPR.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Specificity assessment
- **Affected element** Results section "Binding specificity of the designed peptide to the MLL site of KIX"
- **Evidence pointer** Supplementary Figure 9, location not provided
- **Issue** The specificity assessment shows that the T2857W peptide inhibits the c-Myb-KIX interaction with an IC50 of 16 ± 1 μM, which is approximately threefold higher than the IC50 for the MLL-KIX interaction. However, the wild-type MLL TAD also inhibits c-Myb binding with an IC50 of 36 ± 1 μM. The authors conclude the designed peptide is "more specific" for the MLL site, but the selectivity ratio is modest and the mechanism of cross-inhibition is not discussed.
- **Required correction** Provide a more nuanced discussion of the specificity data, including whether the cross-reactivity is expected given the known ability of MLL TAD to bind the c-Myb site with lower affinity, and whether the selectivity is sufficient for the intended applications.

## Risk / unsupported claims
- The claim that the T2857W peptide has the highest affinity for KIX among all previously reported inhibitors targeting the MLL site is unsupported without a systematic literature comparison.
- The assertion that the design approach "may be useful for rationally developing helical peptides" is weakly supported given the low correlation between computational predictions and experimental outcomes.
- The statement that the T2857W mutation enhances hydrophobic interactions based on the Rosetta model structure is speculative without experimental structural validation.
- The suggestion that the designed peptide "may also inhibit" interactions between KIX and other transcriptional activators is presented without any experimental evidence.
- The claim that the approach could be applied to other protein-protein interactions implicated in disease is a general statement not directly supported by the data presented.