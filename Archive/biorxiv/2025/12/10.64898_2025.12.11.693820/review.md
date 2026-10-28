## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific content, technical soundness, structural biology quality, functional validation, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors report the first crystal structure of a bacterial YQL-family ICL glycosylase (AlkX from Thermobifida fusca) bound to DNA containing an abasic site analog, identify conserved motifs critical for ICL unhooking and DNA binding, and demonstrate that a genetic variant found in a drug-resistant Salmonella enterica strain impairs glycosylase activity
- **Visible evidence base** Crystal structure at 2.6 Å with SAD phasing, in vitro ICL unhooking assays, EMSA binding assays, bacterial growth complementation assays, sequence alignments referenced as Figure S1, structural comparisons to AlkZ
- **Missing materials affecting confidence** Electron density maps (2Fo-Fc, Fo-Fc) not shown; supplementary figures S1-S7 and Tables S1-S2 not provided; no quantitative binding affinities (Kd values); no kinetic parameters for ICL unhooking; no statistical analysis details for growth curves; no raw data for replicate experiments

## Reviewer

- **Overall assessment** This manuscript presents a valuable structural contribution to the understanding of bacterial ICL glycosylases. The crystal structure of TfuAlkX bound to a THF-containing DNA duplex represents the first structure of a YQL-family member and provides mechanistic insight into how these enzymes recognize and process ICLs. The functional validation through mutagenesis, in vitro assays, and in vivo complementation is generally well-executed and supports the major conclusions. However, several technical concerns regarding the structural interpretation, the limited quantitative analysis of binding and activity data, and the somewhat speculative extrapolation to the Salmonella variant warrant attention. The work is of interest to the DNA repair and structural biology communities, though the broader significance for pathogenesis remains partially inferential.

- **Who would be interested in the results, and why** Researchers studying DNA repair mechanisms, particularly ICL repair pathways in bacteria; structural biologists interested in glycosylase-DNA interactions and HTH_42 superfamily proteins; microbiologists studying virulence mechanisms in Acinetobacter baumannii and other nosocomial pathogens; investigators interested in antibiotic resistance mechanisms and the role of DNA repair in bacterial fitness and evolution.

- **Major Strengths** 
  1. First structure of a YQL-family ICL glycosylase, filling a significant gap in the field
  2. Clear identification and functional validation of the DNA binding loop (DBL) as a critical motif
  3. Integration of structural, biochemical, and cellular data to support conclusions
  4. Identification of a clinically relevant variant in Salmonella enterica that impairs activity
  5. Comparative analysis with AlkZ provides insight into substrate specificity differences between YQL and AZL subfamilies

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural evidence
- **Claim pointer** The authors state that the structure reveals "several critical interactions between a bacterial ICL glycosylase and damaged DNA" and that the DBL "partially fills the abasic site void"
- **Evidence pointer** Results section "Crystal structure of AlkX bound to DNA", Figure 1D-F, Figure 2A
- **Concern** The manuscript describes the structure at 2.6 Å resolution but does not present electron density maps for the key structural features. The claim that Y326 "partially fills the abasic site void" and the interpretation of the DBL conformation rely entirely on the refined model. Without showing 2Fo-Fc and Fo-Fc maps contoured at appropriate levels for the DBL, the active site residues, and the THF moiety, the structural interpretations cannot be independently assessed. This is particularly important given that the DBL is described as disordered in the unbound protomer, raising questions about the confidence of the modeled loop in the bound state.
- **Why it matters** The central claim of the paper is the structural basis for lesion recognition. If the electron density for the DBL and active site is ambiguous, the mechanistic conclusions drawn from the structure may be overstated. The absence of map figures prevents reviewers and readers from evaluating the quality of the model in the regions most critical to the paper's conclusions.
- **Resolution test** Provide electron density maps (2Fo-Fc and Fo-Fc) for the DBL region, the active site, and the THF-containing DNA. Show the quality of the density for Y326 and the QxD motif. If the DBL has high B-factors or poor density, this should be acknowledged and the interpretation tempered accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors claim that the DBL mutants "severely curtailed" ICL unhooking and DNA binding, and that the A83P mutation "dramatically reduced" ICL unhooking and binding
- **Evidence pointer** Results section "The DNA binding loop is important for AlkX function", Figure 2B-D, Figure 3D-E
- **Concern** The functional assays are described qualitatively without quantitative metrics. For the ICL unhooking assays, no time courses, rate constants, or endpoint percentages are provided in the text. For the EMSA experiments, no binding affinities (Kd) or even qualitative binding percentages are reported. The growth curves in Figure 2D and 3F lack statistical analysis (error bars, replicates, significance testing). Without these quantitative details, the severity of the mutational effects cannot be assessed, and the comparison between mutants (e.g., Y300A vs. Y300F) is difficult to evaluate.
- **Why it matters** The paper's conclusions about which residues are critical for function depend on the magnitude of the observed effects. Qualitative descriptions such as "severely curtailed" and "reduced" are insufficient to establish the relative importance of different motifs. This is especially important for the A83P variant claim, where the authors suggest a mechanistic explanation for a clinical variant's reduced activity.
- **Resolution test** Provide quantitative data for ICL unhooking assays (e.g., percentage of product at defined time points, with replicates and error bars). For EMSA, report Kd values or at least binding percentages at defined protein concentrations. For growth curves, include statistical analysis with replicates and significance testing.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive extrapolation
- **Claim pointer** The authors state that the A83P variant in Salmonella enterica "likely alters the position of the catalytic motif to consequently impair ICL unhooking activity" and that this provides "a possible mechanistic explanation for how a genetic variant found in an antibiotic-resistant strain of S. enterica inactivates the glycosylase"
- **Evidence pointer** Results section "A genetic variant in S. enterica impairs ICL unhooking", Figure 3B-F
- **Concern** The manuscript tests the A83P mutation in AbaAlkX, not in the actual Salmonella enterica protein. While the authors show that the corresponding mutation in AbaAlkX reduces activity, they do not demonstrate that the Salmonella protein with the A83P variant is actually impaired. The structural context in TfuAlkX (A102) is used to infer the effect, but the Salmonella protein may have additional differences that compensate or exacerbate the mutation's effect. The claim that this provides a "mechanistic explanation" for the clinical variant is therefore somewhat overstated.
- **Why it matters** The clinical relevance of the finding depends on demonstrating that the Salmonella variant is functionally impaired in its native context. Without testing the actual Salmonella protein, the connection between the structural observation and the clinical isolate remains speculative.
- **Resolution test** Test the Salmonella enterica AlkX protein with and without the A83P mutation in ICL unhooking and binding assays. Alternatively, temper the claim to state that the mutation is "predicted to impair" activity based on the AbaAlkX data, without asserting a definitive mechanistic explanation for the clinical variant.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural comparison
- **Claim pointer** The authors state that "comparison of the AlkX and AlkZ structures provides a basis for the substrate differences in the YQL and AZL subfamilies" and that the αF region is "divergent among AZLs"
- **Evidence pointer** Results section "Identification of a putative ICL sensor in AlkX", Figure 4C
- **Concern** The comparison between TfuAlkX and AlkZ is based on a DNA-bound (AlkX) versus DNA-free (AlkZ) structure. The authors acknowledge this limitation but still draw conclusions about substrate specificity differences. The conformational differences in the αF region could simply reflect the presence or absence of DNA rather than intrinsic differences between the subfamilies. Additionally, the modeling of an NM lesion onto the DNA is not described in sufficient detail to assess its reliability.
- **Why it matters** The conclusions about subfamily-specific substrate recognition depend on the validity of the structural comparison. If the observed differences are due to DNA binding rather than intrinsic subfamily properties, the interpretation would be incorrect.
- **Resolution test** Provide a more detailed description of the NM modeling procedure and its limitations. Consider whether an apo AlkX structure or a DNA-bound AlkZ structure would be needed to make definitive comparisons. Alternatively, temper the conclusions about subfamily differences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1B
- **Evidence pointer** Results section "Crystal structure of AlkX bound to DNA"
- **Issue** The asymmetric unit contains two protomers but only one DNA duplex, with one protomer engaged with DNA. The authors note that the DBL is disordered in the unbound protomer. This raises the question of whether the unbound protomer represents a physiologically relevant conformation or an artifact of crystal packing.
- **Required correction** Provide a brief discussion of the oligomeric state of AlkX in solution (e.g., from size exclusion chromatography or multi-angle light scattering) and whether the unbound protomer in the crystal is consistent with a solution state.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** EMSA binding assays
- **Evidence pointer** Methods section "Electrophoretic mobility shift assay (EMSA)"
- **Issue** The EMSA uses a 2F-NM8-ICL substrate with C2'-fluorinated guanines to prevent glycosylase cleavage. The rationale for this substrate is clear, but the manuscript does not state whether the 2F modification affects DNA binding affinity compared to a non-fluorinated substrate.
- **Required correction** Add a sentence noting whether the 2F modification has been previously shown to have minimal effects on binding, or acknowledge this as a potential limitation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Growth curves in Figure 2D and 3F
- **Evidence pointer** Methods section "Bacterial growth curves"
- **Issue** The growth curve experiments appear to be single representative experiments without indication of biological replicates or error bars.
- **Required correction** State the number of biological replicates and include error bars or a statement that the data are representative of at least three independent experiments.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Sequence conservation
- **Affected element** Figure S1
- **Evidence pointer** Results section "Crystal structure of AlkX bound to DNA"
- **Issue** The manuscript states that the DBL is "highly conserved" across YQL/AlkX proteins, but the sequence alignment is only in the supplementary material. The text would benefit from explicitly identifying the conserved residues within the DBL and their positions in the alignment.
- **Required correction** In the text, list the specific conserved residues in the DBL and reference their positions in Figure S1.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "unhooking" is used throughout, which is appropriate for the field. However, the abstract states the structure represents "a product of the ICL unhooking reaction" without specifying that the DNA contains a THF abasic site analog rather than a true abasic site.
- **Required correction** In the abstract, clarify that the DNA contains a synthetic abasic site analog (THF) to avoid any ambiguity about the exact nature of the lesion.

- **Technical failings that need to be addressed before the case is established**
  1. Absence of electron density maps for key structural features (R1-M1)
  2. Lack of quantitative data for functional assays (R1-M2)
  3. Insufficient validation of the Salmonella variant claim in its native context (R1-M3)

- **Assessment against Nature-style criteria**
  - **Originality** The structure of a YQL-family ICL glycosylase bound to DNA is novel and represents a significant advance over the previously determined apo AlkZ structure. The identification of the DBL as a key functional motif is a new contribution.
  - **Scientific importance** The work addresses a fundamental question in DNA repair: how ICL glycosylases recognize and process their substrates. The potential link to pathogenesis in A. baumannii and other clinically relevant bacteria adds translational significance.
  - **Interdisciplinary readership** The work will appeal primarily to DNA repair specialists and structural biologists. The broader microbiology community may find the pathogenesis angle interesting, but the current data do not yet establish a clear link between AlkX activity and virulence beyond the previously published work.
  - **Technical soundness** The structural determination appears sound based on the reported statistics, but the lack of map figures and quantitative functional data limits the ability to fully assess technical quality. The mutagenesis strategy is logical, and the use of multiple assays (in vitro activity, binding, in vivo complementation) is commendable.
  - **Readability for nonspecialists** The manuscript is generally well-written and accessible. The figures are described clearly, and the logic of the experiments is easy to follow. Some sections, particularly the structural description, may be challenging for non-structural biologists, but this is typical for the field.

- **Recommendation posture** Supportive if technical concerns are resolved. The structural data represent a valuable contribution, and the functional validation is largely convincing. However, the absence of electron density maps and quantitative functional data must be addressed before the case is fully established. The Salmonella variant claim should be either validated in the native protein or appropriately tempered.