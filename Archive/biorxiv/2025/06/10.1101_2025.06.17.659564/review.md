## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, figure legends, and supplementary materials
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors propose that full-length MeCP2 requires interactions with nucleosome linker DNA, mediated by a newly identified central region (termed the DNA Interacting Region, DIR), to enable its MBD to read DNA methylation within nucleosome core particles. They further show that histone H1 competes with MeCP2 for linker DNA access, and that disruption of the central DNA-binding motifs reduces MeCP2 binding to methylated nucleosomes in vitro and alters chromatin dynamics in vivo.
- **Visible evidence base** EMSA binding assays, SPR, MST, mass photometry, crosslinking mass spectrometry, FRAP in NIH3T3 cells, hydroxyl radical footprinting, sequence analysis, and mutagenesis
- **Missing materials affecting confidence** No structural data; no quantitative binding affinities for all conditions; no statistical analysis details for FRAP; no raw data for SPR or MST; no validation of the DNMT3A and LEDGF motif comparison beyond sequence alignment

## Reviewer
- **Overall assessment** This manuscript presents a well-executed biochemical dissection of MeCP2-nucleosome interactions, identifying a novel central DNA-binding region that facilitates MBD access to nucleosomal methylation. The use of designer nucleosomes with site-specific methylation is a strength, and the combination of in vitro and in vivo approaches provides complementary evidence. However, several technical concerns regarding the interpretation of binding data, the specificity of the identified motif, and the physiological relevance of the competition experiments need to be addressed before the central claims are fully established.
- **Who would be interested in the results, and why** Researchers studying epigenetic readers, chromatin structure and dynamics, MeCP2 biology, Rett syndrome pathogenesis, and the molecular mechanisms of DNA methylation recognition in chromatin. The identification of a novel DNA-binding region in MeCP2 and the proposed model of linker-dependent methylation reading will be of interest to those working on chromatin-binding proteins and their therapeutic targeting.
- **Major strengths** 1. The use of designer nucleosomes with precisely positioned methylation sites is a rigorous approach that allows unambiguous assignment of binding preferences. 2. The identification of a novel DNA-binding region (DIR) in central MeCP2 is a significant advance. 3. The combination of multiple biophysical techniques (EMSA, SPR, MST, mass photometry) strengthens the binding conclusions. 4. The in vivo FRAP experiments provide functional relevance for the in vitro findings. 5. The H1 competition experiments address an important and debated aspect of MeCP2 biology.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The identification of a novel DNA-binding region in MeCP2 and the linker-dependent model for methylation reading is original and conceptually important. Scientific importance: The findings have implications for understanding MeCP2 function in health and disease, particularly Rett syndrome. Interdisciplinary readership: The work bridges chromatin biology, epigenetics, and neurobiology, and will appeal to a broad audience. Technical soundness: The experimental design is generally rigorous, but several concerns about data interpretation and controls need to be resolved. Readability for nonspecialists: The manuscript is clearly written and the figures are well-organized, though some technical details may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The authors claim that full-length MeCP2 can bind methylation in nucleosome core DNA, but only when linker DNA is present, and that this requires the central region.
- **Evidence pointer** Figure 1D-E, Figure 2, Extended Data Figure 2
- **Concern** The conclusion that MeCP2 binds core methylation is based on EMSA band shifts, but the authors do not demonstrate that the shifted species corresponds to a specific MeCP2-nucleosome complex with the MBD engaged at the methylated core site. The presence of multiple binding modes (e.g., non-specific DNA binding, linker binding) could confound interpretation. The authors should provide direct evidence, such as competition experiments with unmethylated nucleosomes or footprinting of the bound complex, to show that the MBD specifically engages the methylated core site.
- **Why it matters** The central claim of the paper is that MeCP2 can read core methylation when linker DNA is available. If the observed binding is due to non-specific DNA interactions rather than specific MBD-methylation recognition, the conclusion would be substantially weakened.
- **Resolution test** Perform competition experiments with excess unmethylated nucleosomes or DNA, or use a methylation-insensitive MBD mutant to demonstrate that the binding preference for methylated core sites is specifically due to MBD-methylation recognition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental design
- **Claim pointer** The authors claim that the DIR (residues 205-257) is a novel DNA-binding region required for MeCP2-nucleosome interaction.
- **Evidence pointer** Figure 4, Extended Data Figure 6
- **Concern** The DIR construct (MeCP2 205-257) binds DNA in EMSA, but the authors do not show that this region is required for DNA binding in the context of full-length MeCP2. The AT-DIR mut construct contains mutations in both AT-hooks and the DIR, so the contribution of each region to the observed phenotype is not dissected. The authors should test mutations in the DIR alone, or in the AT-hooks alone, to establish the specific requirement for the DIR.
- **Why it matters** The identification of a novel functional region is a key claim. Without dissecting the contributions of individual motifs, the conclusion that the DIR is specifically required is not fully supported.
- **Resolution test** Generate and test full-length MeCP2 with mutations only in the DIR (e.g., K254N, K256N) and compare its binding to nucleosomes with the AT-hook mutations alone and the combined AT-DIR mut.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The authors claim that histone H1 antagonises MeCP2-nucleosome interaction by competing for linker DNA.
- **Evidence pointer** Figure 6, Extended Data Figure 9-10
- **Concern** The H1 competition experiments show that H1 reduces MeCP2 binding, but the mechanism is not directly demonstrated. The authors infer competition for linker DNA, but H1 could also alter nucleosome structure or stability, or directly interact with MeCP2. The claim of competition should be supported by experiments that directly test whether H1 and MeCP2 compete for the same binding site, such as using H1 mutants that lack linker DNA binding or performing competition with linker DNA fragments.
- **Why it matters** The proposed model of H1-MeCP2 competition is an important conceptual advance, but the mechanism needs to be rigorously established to support the model.
- **Resolution test** Use H1 mutants that cannot bind linker DNA (e.g., lacking the C-terminal tail) and test whether they still antagonise MeCP2 binding. Alternatively, perform competition assays with increasing concentrations of free linker DNA to see if it relieves H1-mediated inhibition.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The authors claim that the DIR motif is conserved and found in DNMT3A and LEDGF, suggesting a generalisable DNA-binding module.
- **Evidence pointer** Figure 4C, Extended Data Figure 6E
- **Concern** The sequence similarity between the MeCP2 DIR and the DNMT3A/LEDGF motifs is based on a short sequence (R-P-G-R-K-R-K). The functional relevance of this similarity is only tested for DNMT3A, and the authors do not show that the LEDGF motif binds DNA or that the DNMT3A mutation has the same effect as the MeCP2 mutation. The claim of a generalisable module is speculative without more extensive functional validation.
- **Why it matters** The generalisability of the identified motif is a secondary claim that adds conceptual interest, but it is not essential to the main findings. However, if included, it should be supported by more direct evidence.
- **Resolution test** Test whether the LEDGF motif binds DNA in the same assay, and demonstrate that the DNMT3A mutation affects DNA binding in a manner analogous to the MeCP2 DIR mutation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that MeCP2 "preferentially engages DNA methylation positioned at multiple sites around the nucleosome," but the data show that this preference is dependent on linker DNA and is lost for core methylation without linkers. The abstract could be more precise about this conditionality.
- **Required correction** Revise the abstract to specify that the preference for core methylation is observed only in the presence of linker DNA.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** FRAP data
- **Evidence pointer** Figure 3C, Figure 5C, Extended Data Figure 8
- **Issue** The FRAP data are presented as representative curves and scatter plots, but no statistical analysis (e.g., p-values, confidence intervals) is reported for the differences between wild-type and mutant MeCP2.
- **Required correction** Provide statistical analysis of the FRAP recovery parameters (e.g., mobile fraction, half-time) for all constructs.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Binding isotherms
- **Evidence pointer** Figure 1, Figure 2, Extended Data Figure 2
- **Issue** The binding isotherms are shown for some conditions, but not all. For example, the KD values for MeCP2 binding to unmethylated nucleosomes are not always reported, making it difficult to assess the degree of methylation specificity.
- **Required correction** Report KD values for all conditions tested, including unmethylated controls, in the main text or supplementary tables.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** H1 competition assays
- **Evidence pointer** Figure 6, Extended Data Figure 9-10
- **Issue** The concentration of H1 used in the competition assays is described as "a set concentration," but the exact concentration is not provided in the main text or figure legends.
- **Required correction** Provide the exact H1 concentration used in the competition experiments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** In vivo relevance
- **Evidence pointer** Figure 3C, Figure 5C
- **Issue** The FRAP experiments are performed in NIH3T3 fibroblasts, which are not neuronal cells. The authors should discuss the potential limitations of using a non-neuronal cell line for studying MeCP2 chromatin dynamics, given the neuronal-specific functions of MeCP2.
- **Required correction** Add a sentence in the Discussion acknowledging this limitation and suggesting future experiments in neuronal cells.

## Risk / unsupported claims
- The claim that the DIR is a "novel" DNA-binding region is supported by the data, but the term "novel" should be qualified, as the region overlaps with the previously described transcriptional repression domain (TRD).
- The claim that the DIR motif is "generalisable" based on sequence similarity to DNMT3A and LEDGF is not fully supported, as only DNMT3A was functionally tested.
- The claim that MeCP2 and H1 compete for linker DNA is inferred but not directly demonstrated.
- The physiological relevance of the H1 competition findings is not tested in a cellular context.
- The statement that "MeCP2 combines nonspecific but essential interactions with linker DNA to aid specific binding to nucleosomal methylated DNA, independent of nucleosome structure" is a strong conclusion that is not fully supported by the data, as the authors do not directly test the role of nucleosome structure in the binding mechanism.