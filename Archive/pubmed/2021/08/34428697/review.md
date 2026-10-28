## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and conclusion. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific content, technical soundness, and logical coherence of the claims as presented in the provided text. No assessment of editorial fit or publication venue.
- **Shared manuscript claim summary** The manuscript reports that DNA sequence context alone can determine whether the Rad4/XPC nucleotide excision repair complex can unwind ("open") a DNA site, even when the protein is artificially tethered to ensure prolonged residence. A sequence with consecutive C/Gs (CCC/GGG) is opened, while an alternating C/G sequence (CGC/GCG) resists opening and instead induces a 180°-reversed binding mode capping the DNA end. The authors support this with crystallography, fluorescence lifetime (FLT)-FRET solution studies, and molecular dynamics (MD) simulations, and propose implications for lesion repair propensity and mutational hot/cold spots.
- **Missing materials affecting confidence** Supplementary figures (S1–S12), tables (S1–S5), movies (S1–S2), and detailed methods for MD simulations and competitive EMSA are referenced but not provided. These are essential for full evaluation of the technical claims.

## Reviewer
- **Overall assessment** This is a well-structured and technically sophisticated study that addresses an important question in nucleotide excision repair: whether local DNA sequence can intrinsically determine the "openability" of a site by Rad4/XPC. The combination of crystallography, solution FRET, and MD simulation is powerful and mutually reinforcing. The central claim, that CGC/GCG resists opening while CCC/GGG is opened under identical tethering conditions, is supported by the presented data. However, the absence of key supplementary materials limits full verification of several technical details, particularly the MD simulation protocols and the EMSA controls. The manuscript would be strengthened by clarifying the relationship between the "reverse mode" binding and the physiological scanning mechanism, and by discussing whether the observed sequence effects are generalizable beyond the specific constructs tested.
- **Who would be interested in the results, and why** Researchers in DNA repair, particularly those studying nucleotide excision repair mechanisms, lesion recognition, and the role of DNA sequence context in repair efficiency. Also relevant to computational biologists studying DNA conformational dynamics and protein-DNA interactions, and to cancer biologists interested in mutational signatures and hot/cold spot mutagenesis.
- **Major strengths**
  1. The study addresses a fundamental and previously unresolved question: whether DNA sequence alone can dictate the outcome of Rad4/XPC binding, independent of lesion presence or protein residence time.
  2. The use of three orthogonal approaches (crystallography, FLT-FRET, MD simulation) provides convergent evidence for the central claim.
  3. The "reverse mode" crystal structure is a novel and potentially important finding, representing the first 3D structure of Rad4 bound to a DNA end.
  4. The FLT-FRET temperature-dependence experiments elegantly demonstrate local pre-melting in CCC/GGG but not CGC/GCG, providing a mechanistic basis for the observed difference.
  5. The manuscript is clearly written and the logical flow from observation to mechanism to implication is easy to follow.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that MD simulations show CCC/GGG has higher intrinsic slide, roll, and untwist, and weaker base stacking than CGC/GCG, and that these differences explain the differential "openability."
  - **Evidence pointer** Methods section "MD simulations and structural analyses" (details in SI, not provided); Figures 5 and 6; Figure S10–S12 (not provided)
  - **Concern** The MD simulation methods are only described as "full details are given in the SI Methods," which is not provided. Critical parameters such as force field, water model, salt concentration, simulation length, number of replicates, and analysis protocols are absent. Without these, the reproducibility and statistical robustness of the simulation results cannot be assessed. Furthermore, the claim that the free CCC/GGG DNA is "pre-distorted" toward the open conformation relies on comparison to ideal B-DNA, but the reference state and the significance thresholds for the reported differences are not defined.
  - **Why it matters** The MD simulations are a key pillar of the mechanistic argument. If the simulation protocols are not standard or the analyses are not statistically robust, the conclusion that intrinsic conformational differences drive the differential opening would be weakened. The reader cannot verify this without the missing methods.
  - **Resolution test** Provide the full MD simulation methods in the main text or supplement, including force field parameters, simulation length, equilibration protocol, number of replicates, and error estimates for all reported quantities. Show that the differences between CCC/GGG and CGC/GCG are statistically significant and reproducible across independent simulations.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that the FLT-FRET data show that CGC/GCG remains predominantly B-DNA-like even when tethered to Rad4, while CCC/GGG adopts open conformations.
  - **Evidence pointer** Results section "Matched DNA containing alternating CG/GC is resistant to 'opening' by tethered Rad4 in solution"; Figures 3 and S6; Tables S3–S5 (not provided)
  - **Concern** The FLT-FRET analysis relies on fitting lifetime distributions with multiple Gaussian components and assigning each component to a specific conformational state. The assignment of the long-lifetime component (~4.8 ns) to a "zero-FRET" conformation is discussed, but the possibility that this component arises from free dye or partially labeled DNA is not fully excluded. The authors state that unpaired donor strands were ruled out in previous studies, but the controls for the specific constructs used here are not shown. Additionally, the fractional populations are reported with standard deviations from three measurements, but the statistical significance of the differences between free and tethered conditions is not tested.
  - **Why it matters** The FLT-FRET data are the primary solution-phase evidence that CGC/GCG resists opening. If the assignment of lifetime components to conformations is ambiguous, or if the differences are not statistically significant, the conclusion that CGC/GCG is "resistant" would be less robust.
  - **Resolution test** Provide the raw FLT decay curves, the fitted lifetime distributions for all replicates, and the results of statistical tests (e.g., t-tests or ANOVA) comparing the fractional populations between conditions. Include control experiments showing that the long-lifetime component is not due to free dye or incomplete labeling.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation / Generalizability
  - **Claim pointer** The manuscript claims that the "reverse mode" binding observed with CGC/GCG represents a distinct, sequence-dependent outcome and that this may have implications for how Rad4/XPC scans DNA and recognizes lesions.
  - **Evidence pointer** Results section "Matched DNA with alternating CG/GC repeats fails to be 'opened' by tethered Rad4"; Discussion section "Implications of DNA-end binding"
  - **Concern** The "reverse mode" structure was obtained with a 23-bp DNA and a mutant Rad4 lacking the β-hairpin3 tip. The authors argue that the DNA length difference is unlikely to be the cause, but this is not rigorously demonstrated. More importantly, the physiological relevance of the "reverse mode" is speculative. The authors suggest it may be relevant to DNA-end binding during scanning or transcription, but no functional data are provided to support this. The claim that this is the "first 3D structure" of Rad4 bound to a DNA end is interesting, but its significance for the central thesis of the paper (sequence-dependent openability) is not fully integrated.
  - **Why it matters** The "reverse mode" is presented as a key piece of evidence that CGC/GCG resists opening. If this binding mode is an artifact of the specific construct (e.g., the mutant protein or the short DNA), the conclusion that the sequence itself is resistant would be weakened. The speculative implications for DNA-end binding, while interesting, are not supported by direct evidence.
  - **Resolution test** Provide additional experiments or analyses showing that the "reverse mode" is not an artifact of the mutant protein or DNA length. For example, test whether WT Rad4 also forms the "reverse mode" with CGC/GCG, or whether longer CGC/GCG-containing DNAs also resist opening. Alternatively, temper the claims about physiological relevance and present the "reverse mode" as a structural observation that supports the sequence-dependent resistance, without over-interpreting its functional significance.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, first sentence
  - **Issue** The phrase "DNA 'opening'" is used without prior definition. While the concept is explained in the introduction, the abstract would benefit from a brief clarification of what "opening" means in this context (i.e., local unwinding and base flipping by Rad4).
  - **Required correction** Add a brief parenthetical definition, e.g., "DNA 'opening' (local unwinding and base flipping)" in the abstract.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical clarity
  - **Affected element** Results section, FLT-FRET analysis
  - **Evidence pointer** Results section "Matched DNA containing alternating CG/GC is resistant to 'opening' by tethered Rad4 in solution"; Figure 3
  - **Issue** The description of the FLT-FRET data is dense and the reader must refer to multiple supplementary tables and figures to follow the analysis. The main text would benefit from a clearer summary of the key quantitative differences between CCC/GGG and CGC/GCG, such as the fractional populations of the B-DNA-like component under each condition.
  - **Required correction** Add a sentence in the main text explicitly stating the fractional population of the B-DNA-like component for free vs. tethered CGC/GCG and CCC/GGG, with the corresponding uncertainties.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section "Implications of the 'openability' of C/G-rich sequences with consecutive C/Gs"
  - **Issue** The discussion of non-NER functions of Rad4/XPC, while interesting, is somewhat tangential and not directly supported by the data presented. The connection between the sequence-dependent openability observed here and the proposed roles in transcription or base excision repair is speculative.
  - **Required correction** Either provide a brief caveat that these implications are speculative and require further investigation, or shorten this section to keep the focus on the NER-related implications.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, crystallization
  - **Evidence pointer** Methods section "Crystallization of Δβ−hairpin3 mutant crosslinked with the CGC/GCG DNA duplex"
  - **Issue** The crystallization conditions are described, but the resolution of the diffraction data and the final R/Rfree values are only mentioned in the results (2.9 Å, R/Rfree 22%/27%). The completeness and multiplicity of the data are not stated.
  - **Required correction** Add a sentence in the methods or results stating the data completeness and multiplicity for the final structure.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion, comparison with previous work
  - **Evidence pointer** Discussion section "Importance of sequence context on lesion recognition and NER"
  - **Issue** The discussion of previous studies on sequence context effects is brief and does not fully contextualize the novelty of the current findings. For example, the authors mention that sequence context has been studied before, but do not clearly state what is new about their observation that a matched, undamaged sequence can resist opening even under tethering.
  - **Required correction** Add a sentence explicitly stating what is novel about the current study compared to previous work on sequence context in NER.

## Risk / unsupported claims
- The claim that the "reverse mode" structure represents a physiologically relevant DNA-end binding mode is speculative and not directly supported by functional data.
- The claim that the sequence-dependent openability observed here can help explain mutational hot and cold spots in genomic DNA is plausible but not directly tested in this study.
- The MD simulation results, as presented, cannot be fully evaluated without the detailed methods and convergence analyses provided in the missing supplementary material.
- The FLT-FRET assignment of the long-lifetime component to a "zero-FRET" conformation is not fully validated for the specific constructs used here, as the relevant control experiments are not shown.
- The statement that the "reverse mode" is the first 3D structure of Rad4 bound to a DNA end is a claim of priority that cannot be verified from the provided material alone.