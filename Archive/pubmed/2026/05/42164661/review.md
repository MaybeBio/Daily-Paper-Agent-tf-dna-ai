## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, figure legends, and supplementary information descriptions.
- **Assessment boundary** Scientific content, methodological rigor, logical coherence, and support of claims by presented evidence. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors propose that the local mechanostructural properties of protein cargoes, specifically the mechanical stability and structural disorder of the region adjacent to the nuclear localization signal (NLS), regulate the rate and directionality of nucleocytoplasmic transport through the nuclear pore complex (NPC). They support this with optogenetic transport assays, single-molecule magnetic tweezers, steered molecular dynamics simulations, biochemical binding assays, and a bioinformatic survey of human transcription factors.
- **Visible evidence base** Main text figures 1–6, extended data figures 1–10, supplementary figures 1–28, supplementary table 1, methods section, and source data descriptions.
- **Missing materials affecting confidence** Raw numerical data for all figures, full statistical analysis details, complete simulation parameters, and the full supplementary information content are not provided in the submitted material. The manuscript states these are available but they were not included in the review package.

## Reviewer
- **Overall assessment** This manuscript presents a compelling and well-executed study that extends previous work on the role of mechanical stability in nuclear transport. The combination of experimental and computational approaches is impressive, and the central finding that local, rather than global, mechanical properties determine transport orientation is novel and significant. The study is generally rigorous, but several concerns regarding quantitative rigor, mechanistic depth, and generalizability need to be addressed before the conclusions are fully established.
- **Who would be interested in the results, and why** Researchers in nucleocytoplasmic transport, mechanobiology, single-molecule biophysics, and protein engineering. The findings have implications for understanding how cells regulate transcription factor localization and for designing proteins with controlled nuclear trafficking. The work bridges biophysics and cell biology in a way that will appeal to a broad readership.
- **Major strengths**
  1. The central hypothesis is clearly formulated and directly tested with a well-designed optogenetic system that allows precise control of transport direction.
  2. The combination of single-molecule magnetic tweezers, SMD simulations, and cellular assays provides a multi-scale view of the mechanism.
  3. The use of circular permutation to alter mechanical stability without changing the primary sequence is an elegant and powerful approach.
  4. The bioinformatic analysis of human transcription factors suggests potential biological relevance beyond the model proteins.
  5. The writing is clear and the logic is easy to follow.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Quantitative rigor
  - **Claim pointer** The authors claim that the import rate is "significantly higher" for the import-forward construct compared with the import-reverse construct, and that this difference is due to the local mechanical stability of the N-terminus.
  - **Evidence pointer** Figure 1d,e and associated text
  - **Concern** The statistical analysis of the kinetic parameters (kI, Ke) is not fully described. The authors report p-values from a Mann-Whitney test, but do not provide effect sizes, confidence intervals, or the number of independent experiments. More importantly, the kinetic model used to extract kI assumes first-order kinetics, but the validity of this assumption is not tested. The authors should provide a more complete statistical treatment, including a demonstration that the model adequately fits the data, and should report the variability across independent experiments.
  - **Why it matters** The central conclusion of the paper rests on the quantitative difference in import rates between the two orientations. Without a rigorous statistical framework, it is difficult to assess the robustness of this difference.
  - **Resolution test** Provide full statistical details, including the number of independent experiments, effect sizes, and confidence intervals. Show representative fits of the kinetic model to individual cell traces and demonstrate that the model is appropriate. Consider using a model-free analysis to confirm the difference in transport rates.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** No
  - **Axis** Mechanistic depth
  - **Claim pointer** The authors propose that the lower local mechanical stability of the N-terminus leads to partial unfolding, which enhances transport. They further propose that this is due to increased exposure of hydrophobic residues that interact with FG-Nups.
  - **Evidence pointer** Figure 2n, Extended Data Figure 10, and associated text
  - **Concern** The proposed mechanism is plausible but not directly tested. The authors show a correlation between mechanical stability and transport rate, and they show that unstructured regions have higher affinity for FG-Nups, but they do not demonstrate that partial unfolding actually occurs during transport in cells. The link between the in vitro mechanical measurements and the in vivo transport rates is inferred, not established.
  - **Why it matters** The paper's title and central claim are about the mechanism. Without direct evidence of partial unfolding during transport, the proposed mechanism remains a hypothesis.
  - **Resolution test** Perform experiments that directly probe the conformational state of the cargo during transport, for example using FRET-based sensors or by trapping unfolding intermediates. Alternatively, use mutants that specifically disrupt the proposed hydrophobic interactions to show that they are required for the orientation-dependent transport.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability
  - **Claim pointer** The authors state that "the rate of both nuclear import and export is enhanced when the translocating protein is threaded through the nuclear pore from the specific region exhibiting lower local nanomechanical stability and increased structural disorder" and that this applies to "a range of model proteins."
  - **Evidence pointer** Figures 1–5 and Extended Data Figures 5–6
  - **Concern** The study uses a limited set of model proteins, all of which are relatively small and well-folded. It is not clear if the findings extend to larger, multi-domain proteins, intrinsically disordered proteins, or proteins that form stable oligomers. The authors should discuss the limitations of their model system and the conditions under which their proposed mechanism might not apply.
  - **Why it matters** The claim of generality is important for the paper's impact. If the mechanism only applies to a narrow class of proteins, the significance is reduced.
  - **Resolution test** Test additional proteins with different folds, sizes, and mechanical stabilities. Include a protein that is intrinsically disordered or a multi-domain protein to see if the orientation effect is still observed.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Control experiments
  - **Claim pointer** The authors conclude that the orientation-dependent transport is due to the mechanical properties of the cargo, not the specific sequence or position of the NLS.
  - **Evidence pointer** Figure 3 and associated text
  - **Concern** The authors test different NLS sequences and show that the orientation effect is enhanced with higher-affinity NLS. However, they do not test whether the position of the NLS relative to the mechanically weak region is the critical factor, or whether the effect is simply due to the NLS being closer to the terminus. A control where the NLS is placed at the same position but the mechanical stability of the two termini is swapped (e.g., using a circular permutant with the weak region at the C-terminus) would be more definitive.
  - **Why it matters** The conclusion that the mechanical properties, not the NLS position, are the key determinant is central to the paper. Without this control, an alternative explanation is possible.
  - **Resolution test** Design a construct where the NLS is at the N-terminus but the mechanically weak region is at the C-terminus (or vice versa) and show that the transport rate follows the mechanical stability, not the NLS position.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1b
  - **Evidence pointer** Figure 1b
  - **Issue** The schematic of the import-forward and import-reverse constructs is not entirely clear. It would be helpful to label the N- and C-termini of each domain and to indicate the direction of transport more explicitly.
  - **Required correction** Add clear labels to the schematic and consider adding a cartoon of the NPC to illustrate the direction of transport.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, SMD simulations
  - **Evidence pointer** Methods section
  - **Issue** The description of the SMD simulations is brief. The authors should provide more details on the system setup, equilibration, and the number of replicates. It is also unclear how the pulling speed was chosen and whether the results are converged.
  - **Required correction** Expand the methods section to include full simulation details, including system size, simulation time, and convergence criteria.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of export results
  - **Evidence pointer** Figure 5 and associated text
  - **Concern** The export experiments show a smaller orientation effect than import. The authors attribute this to a "lesser degree" of sensitivity, but do not discuss why this might be the case. A brief discussion of the potential differences between the import and export machinery would be helpful.
  - **Required correction** Add a sentence or two discussing possible reasons for the reduced asymmetry in export.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 6
  - **Evidence pointer** Figure 6
  - **Issue** The disorder analysis in Figure 6l is presented as a single example. It would be useful to show the distribution of disorder scores for all 305 TFs analyzed, perhaps as a histogram or violin plot.
  - **Required correction** Add a supplementary figure showing the distribution of disorder scores for all analyzed TFs.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Incomplete statistical analysis of the key kinetic measurements.
  - R1-M2: Lack of direct evidence for the proposed partial unfolding mechanism.
  - R1-M4: Missing control experiment to rule out NLS position as the primary determinant.
- **Assessment against Nature-style criteria**
  - **Originality** High. The concept of local mechanical anisotropy within a single domain determining transport direction is novel and extends previous work on global stability.
  - **Scientific importance** High. The findings have implications for understanding the regulation of transcription factor localization and for the design of proteins with controlled nuclear trafficking. The work bridges biophysics and cell biology.
  - **Interdisciplinary readership** Broad. The work will appeal to researchers in biophysics, cell biology, and protein engineering.
  - **Technical soundness** Generally good, but with the concerns noted above regarding statistical rigor and mechanistic proof. The combination of techniques is a strength, but the link between in vitro mechanics and in vivo transport needs to be strengthened.
  - **Readability for nonspecialists** Good. The paper is well-written and the logic is clear. The use of figures is effective.
- **Recommendation posture** Supportive if technical concerns are resolved. The central finding is novel and significant, but the quantitative rigor and mechanistic depth need to be improved to fully support the claims.

## Risk / unsupported claims
- The claim that the mechanism involves partial unfolding and exposure of hydrophobic residues is not directly supported by the data presented.
- The claim that the findings apply broadly to "a range of model proteins" is only supported for a limited set of small, well-folded domains.
- The bioinformatic analysis of human TFs is suggestive but does not establish a causal link between disorder and transport rate.
- The quantitative values of the kinetic parameters (kI, Ke) are presented without full statistical context, making it difficult to assess their reliability.