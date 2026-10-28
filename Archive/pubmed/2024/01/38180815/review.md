## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, and figure legends as provided.
- **Assessment boundary** Scientific soundness, logical coherence, experimental support for claims, and technical adequacy based solely on the supplied text. No external data, supplementary figures, or unpublished materials were accessed.
- **Shared manuscript claim summary** The authors propose that Rif2, through its MIN motif, binds Rad50 and stimulates ATP hydrolysis, inducing an ADP-bound MRX conformation that is incompatible with Tel1 binding. This reduces Tel1 recruitment to DSBs, thereby inhibiting Tel1-dependent checkpoint signalling and DSB end-tethering. A hypermorphic Tel1 variant (Tel1hy909) that increases Tel1 persistence at DSBs suppresses the tethering defect, supporting a direct structural role for Tel1 in bridging DSB ends.
- **Visible evidence base** Results sections describing AlphaFold-Multimer modelling, yeast two-hybrid assays, spot tests, ChIP-qPCR, co-immunoprecipitation, DSB resection assays, hairpin cleavage assays, SSA repair assays, and ATPase assays. Figures referenced: Figures 1–7, Supplementary Figures S1.
- **Missing materials affecting confidence** Supplementary Tables S1–S3, Supplementary Figures S1A–D, full uncropped blots, raw quantification data, statistical details for each comparison, and the complete AlphaFold-Multimer output metrics. These are referenced but not provided in the submitted text.

## Reviewer
- **Overall assessment** This manuscript presents a coherent and mechanistically detailed model for how Rif2 negatively regulates Tel1 at DNA double-strand breaks. The use of AlphaFold-Multimer to guide mutagenesis, followed by validation through genetic and biochemical assays, is a strong approach. The key claims—that Rif2S6E enhances Rif2-Rad50 interaction, reduces Tel1 recruitment without affecting MRX occupancy, and impairs DSB tethering in a Tel1-dependent manner—are logically connected and largely supported by the presented data. However, several technical details and quantitative validations are missing, and some conclusions extend beyond the direct evidence. The work is of high interest to the DNA repair and checkpoint signalling communities.
- **Who would be interested in the results, and why** Researchers studying DNA double-strand break repair, checkpoint activation, the MRX/MRN complex, ATM/Tel1 signalling, and telomere biology. The proposed mechanism—Rif2-induced ATP hydrolysis switching MRX to a Tel1-incompatible state—has broad implications for understanding how ATPase cycles in sensor complexes regulate downstream kinase recruitment. The structural predictions and mutagenesis strategy may also interest computational biologists and protein engineers.
- **Major strengths** 1) The study addresses a long-standing question about how Rif2 inhibits Tel1 with a clear mechanistic hypothesis. 2) The combination of structural prediction, targeted mutagenesis, and in vivo functional assays is rigorous and mutually reinforcing. 3) The separation of MRX occupancy from Tel1 recruitment is a clean experimental distinction that strengthens the direct-inhibition model. 4) The use of a hypermorphic Tel1 allele to rescue tethering provides genetic evidence for a causal link. 5) The writing is clear and the logical flow from modelling to mechanism is easy to follow.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (AlphaFold-Multimer validation), R1-M2 (ATPase assay conditions and interpretation), R1-M3 (quantification and statistics), R1-M4 (tethering assay specificity).
- **Assessment against Nature-style criteria**  
  *Originality*: High. The proposed mechanism—Rif2 acting as an ATPase-stimulating factor that switches MRX to a Tel1-incompatible state—is novel and not merely incremental.  
  *Scientific importance*: High. Tel1/ATM signalling and DSB repair are fundamental processes; understanding how a negative regulator works at the molecular level has broad implications.  
  *Interdisciplinary readership*: Moderate. The work is primarily of interest to the DNA repair and checkpoint fields. The structural modelling component may attract computational biologists, but the overall scope is specialised.  
  *Technical soundness*: Moderate. The genetic and cell-based assays are generally well executed, but the biochemical ATPase data and structural validation require additional controls and quantitative support.  
  *Readability for nonspecialists*: Good. The manuscript is clearly written, with a logical progression and helpful figure references. Some specialised terms (e.g., MIN, MRX, SSA) are defined early.
- **Recommendation posture** Supportive if technical concerns are resolved. The core model is compelling and the genetic data are strong, but the biochemical and structural evidence needs strengthening before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural modelling validation
- **Claim pointer** The authors state that AlphaFold-Multimer modelling "pinpointed" the interaction surface between Rif2 MIN and Rad50, and that the predicted interface is validated by subsequent mutagenesis.
- **Evidence pointer** Results section "Analysis of the binding interface between the Rif2 MIN and Rad50", Figure 1B–D, Supplementary Figure S1A–D.
- **Concern** The AlphaFold-Multimer model is presented as a central tool for identifying the interaction interface, but the validation is indirect. The authors show that mutations in the predicted interface (V18E, I23E) reduce Rif2 function, and that S6E enhances interaction. However, no direct structural validation (e.g., co-crystal structure, cross-linking, or NMR) is provided. The model's accuracy is inferred solely from functional correlation. Additionally, the statement that the prediction is "high-confidence" is based on pLDDT and ipTM scores, but these metrics do not guarantee correct inter-domain orientation or interface prediction.
- **Why it matters** The entire mechanistic model rests on the assumption that the predicted interface is biologically relevant. If the interface is incorrect, the interpretation of the S6E and other mutations could be misleading. Direct structural validation or at least a more rigorous computational cross-validation (e.g., docking with experimental restraints) is needed.
- **Resolution test** Provide experimental evidence for the direct interaction, such as co-immunoprecipitation with purified proteins, isothermal titration calorimetry, or mutagenesis of Rad50 residues predicted to contact Rif2 and demonstration of loss of binding. Alternatively, a high-resolution structure of the Rif2-Rad50 complex would fully resolve this concern.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biochemical assay interpretation
- **Claim pointer** The authors claim that Rif2S6E stimulates Rad50 ATPase activity more efficiently than wild-type Rif2, and that this increased ATPase activity induces an ADP-bound MRX conformation unsuitable for Tel1 binding.
- **Evidence pointer** Results section "Rif2S6E limits Tel1–MRX interaction", Figure 7A.
- **Concern** The ATPase assay is described only briefly. The authors state that Rif2S6E increases ATP hydrolysis by Rad50 more efficiently than wild-type Rif2, but no kinetic parameters (e.g., Vmax, Km) or dose-response curves are shown. It is unclear whether the effect is due to increased binding affinity, increased catalytic turnover, or a combination. Moreover, the connection between ATPase stimulation and Tel1 release is inferred but not directly demonstrated. The authors do not show that the ADP-bound state of MRX is indeed the state that fails to bind Tel1. This is a critical mechanistic link.
- **Why it matters** The model proposes a specific conformational state (ADP-bound) as the Tel1-incompatible form. Without direct evidence that ATP hydrolysis and ADP accumulation are necessary and sufficient for Tel1 release, the model remains speculative. The ATPase data are also not quantitatively robust enough to support the claim of "more efficient" stimulation.
- **Resolution test** Provide full ATPase kinetics (e.g., Michaelis-Menten plots) for wild-type Rif2 and Rif2S6E. Use non-hydrolysable ATP analogues (e.g., AMP-PNP) or Rad50 ATPase mutants to test whether ATP hydrolysis is required for Tel1 release. Directly measure Tel1-MRX interaction in the presence of ATP, ADP, or AMP-PNP to demonstrate the conformational dependence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative data and statistics
- **Claim pointer** The manuscript makes several quantitative claims, including "reduced Tel1 activation," "decreased Tel1 association with DSBs," and "impaired DSB end-tethering," but the supporting data are presented without clear statistical analysis.
- **Evidence pointer** Results sections "Rif2S6E reduces Tel1 activation by decreasing Tel1 association with DSBs" and "Rif2S6E impairs DSB end-tethering and DSB repair by SSA", Figures 4, 5, 6.
- **Concern** For ChIP-qPCR, tethering assays, and SSA repair, the authors show representative experiments or bar graphs, but the number of biological replicates, error bars, and p-values are not consistently reported. The methods section mentions statistical analysis using a t-test, but the specific comparisons and significance thresholds are not stated in the results. This makes it difficult to assess the robustness of the conclusions.
- **Why it matters** Quantitative claims require appropriate statistical support. Without clear reporting of replicates and significance, the reader cannot determine whether the observed differences are reproducible and meaningful.
- **Resolution test** Provide full statistical details for all quantitative experiments, including the number of independent biological replicates, the type of test used, and the exact p-values for each comparison. Add error bars to all graphs and state the significance level in the figure legends.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Tethering assay specificity
- **Claim pointer** The authors conclude that Rif2S6E impairs DSB end-tethering and that this defect is due to reduced Tel1 association, based on the LacI-GFP foci assay.
- **Evidence pointer** Results section "Rif2S6E impairs DSB end-tethering and DSB repair by SSA", Figure 6A, 6B, 6F.
- **Concern** The LacI-GFP foci assay measures the physical proximity of two loci, but it does not directly measure tethering strength or the molecular mechanism. The authors show that rif2-S6E cells have more two-foci events, but they do not rule out other explanations, such as altered chromatin structure, changes in DSB mobility, or indirect effects on cell cycle progression. The suppression by Tel1hy909 is supportive but does not fully exclude these alternatives.
- **Why it matters** The conclusion that Tel1 has a direct structural role in tethering is a strong claim. If the tethering defect is an indirect consequence of other changes, the model would need revision.
- **Resolution test** Perform complementary assays, such as chromatin conformation capture (3C) or live-cell imaging of DSB dynamics, to confirm the tethering defect. Use a Tel1 mutant that cannot bind MRX but retains kinase activity to test whether binding or kinase activity is required for tethering.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure legends
- **Affected element** Figures 1–7
- **Evidence pointer** All figure legends
- **Issue** Some figure legends are incomplete. For example, Figure 1C and 1D do not specify how the polar contacts were identified or whether they are predicted or experimentally confirmed. Figure 7A does not state the concentration of ATP used or the reaction time.
- **Required correction** Expand figure legends to include all experimental conditions, definitions of abbreviations, and the number of replicates. Clearly distinguish between predicted and experimentally validated interactions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Abstract, Introduction, Results
- **Evidence pointer** Throughout
- **Issue** The terms "MRX" and "MRX complex" are used interchangeably. The term "MRVMX" is introduced in the Results section without definition. This is confusing.
- **Required correction** Define "MRVMX" at first use and use consistent terminology throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The authors do not discuss alternative explanations for their findings, such as the possibility that Rif2S6E affects Tel1 recruitment indirectly through changes in chromatin structure or other protein interactions.
- **Required correction** Add a paragraph in the Discussion addressing alternative models and explaining why the proposed mechanism is the most parsimonious explanation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability statement
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The statement "All relevant data are included in the manuscript and the Supplementary Data file" is vague. It is unclear whether raw data (e.g., uncropped blots, raw ChIP-qPCR values) are available.
- **Required correction** Specify exactly which data are available and where. Consider depositing raw data in a public repository.

## Risk / unsupported claims
- The claim that Rif2S6E induces an "ADP-bound MRX conformation that is not suitable for Tel1 binding" is inferred from indirect evidence (ATPase activity and reduced Tel1-MRX co-IP) but not directly demonstrated. This is a central mechanistic claim that requires direct conformational or binding studies.
- The claim that Tel1 has a "direct and structural role" in DSB end-tethering is supported by genetic suppression data but lacks direct biochemical or biophysical evidence. The possibility of indirect effects is not fully excluded.
- The statement that the AlphaFold-Multimer model is "high-confidence" is based on computational metrics, but the accuracy of the specific interface prediction is not experimentally validated. This should be stated more cautiously.
- The claim that Rif2S6E "enhances the inhibitory effect" of Rif2 is based on phenotypic assays (DNA damage sensitivity, tethering) but the quantitative extent of enhancement is not clearly defined.