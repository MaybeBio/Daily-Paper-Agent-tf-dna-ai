## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report the synthesis of a novel doubly-sulfonylated imidazolone compound, Stomidazolone, via a newly developed amination reaction. They demonstrate that Stomidazolone inhibits stomatal differentiation in Arabidopsis by directly binding to the ACTL domain of the bHLH transcription factor MUTE, thereby perturbing its heterodimerization with SCREAM. Structure-guided engineering of MUTE variants with reduced Stomidazolone binding confers resistance in vivo, validating the proposed mechanism.
- **Visible evidence base** Abstract, Introduction, Results (including Figures 1-7 and Supplementary Figures 1-12), Discussion, Methods, and Supplementary Tables 1-6
- **Missing materials affecting confidence** Raw source data files, full NMR spectra for all synthesized compounds, complete crystallographic data tables, and detailed statistical outputs are referenced but not fully available in the provided text

## Reviewer
- **Overall assessment** This manuscript presents a compelling and well-executed study that identifies a novel chemical inhibitor of stomatal differentiation. The work combines synthetic chemistry, forward chemical genetics, biophysical analysis, and in vivo validation to establish a clear mechanism of action. The identification of Stomidazolone as a direct binder of the MUTE ACTL domain and its ability to disrupt SCRM-MUTE heterodimerization is novel and significant. The study is technically rigorous, with multiple complementary approaches supporting the central claims. The engineering of Stomidazolone-resistant MUTE variants is a particularly strong validation of the proposed mechanism. The manuscript is well-written and will be of interest to plant developmental biologists, chemical biologists, and those studying bHLH transcription factor regulation.
- **Who would be interested in the results, and why** Plant developmental biologists studying stomatal lineage specification and bHLH transcription factor function will find this work directly relevant. Chemical biologists interested in small-molecule modulators of protein-protein interactions, particularly those targeting transcription factors, will be interested in the novel scaffold and mechanism. Researchers studying the ACTL domain as a regulatory module in plant bHLH proteins will find the structural insights valuable. The work may also appeal to those interested in chemical genetics approaches for manipulating plant development, with potential agricultural applications.
- **Major strengths** The study is notable for its comprehensive approach, combining synthetic chemistry with forward genetics, biophysics, and in vivo validation. The identification of a small molecule that specifically targets the ACTL domain of a bHLH transcription factor is a significant advance. The use of multiple orthogonal assays (Y2H, BiFC, ITC, BLI) to establish the mechanism is rigorous. The engineering of resistant MUTE variants provides definitive evidence for the on-target mechanism. The chemical synthesis is novel and the compound is stable under biological conditions, supporting its utility.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Specificity and off-target effects
  - **Claim pointer** The authors claim that Stomidazolone "directly and primarily targets the ACTL domain of MUTE" and that its in vivo effects are due to specific disruption of SCRM-MUTE heterodimerization.
  - **Evidence pointer** Figure 6, Supplementary Figures 5-9, Discussion
  - **Concern** While the authors demonstrate that Stomidazolone binds to MUTE with higher affinity than to SPECTACLE, FAMA, or SCRAM, the in vitro binding data show that it also binds to these other bHLH proteins, albeit with lower affinity. The in vivo selectivity is inferred from phenotypic analyses, but the manuscript does not directly demonstrate that Stomidazolone does not affect other bHLH-ACTL protein functions in planta. Given that the compound is applied at 50-100 µM, off-target effects on other bHLH-ACTL proteins cannot be excluded. The authors should address the potential for off-target effects, perhaps by transcriptomic or proteomic analysis, or by testing additional bHLH-ACTL mutants.
  - **Why it matters** The central claim of the paper is that Stomidazolone is a selective inhibitor of MUTE. If the compound has broader effects on other bHLH-ACTL proteins, the interpretation of the phenotypic data and the proposed mechanism would be weakened. Establishing selectivity is critical for the compound's utility as a tool and for the validity of the mechanistic conclusions.
  - **Resolution test** The authors should provide additional evidence of selectivity, such as transcriptomic profiling of Stomidazolone-treated seedlings compared to mute mutants, or demonstrate that Stomidazolone does not affect the function of other bHLH-ACTL proteins in vivo using available mutants or reporters.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic detail of heterodimer disruption
  - **Claim pointer** The authors state that Stomidazolone "perturbs the SCRM-MUTE heterodimerization" and that this is the primary mechanism of action.
  - **Evidence pointer** Figure 6, Supplementary Figures 5-9
  - **Concern** The biophysical data (ITC, BLI) demonstrate that Stomidazolone binds to MUTE and reduces its affinity for SCRAM. However, the manuscript does not provide a detailed mechanistic model for how binding to the ACTL domain disrupts heterodimerization. Does Stomidazolone induce a conformational change in the ACTL domain? Does it sterically block the interaction interface? The docking model (Figure 7) provides a static picture, but no dynamic or mutational analysis is presented to test the predicted binding mode beyond the alanine substitutions. A more detailed understanding of the mechanism would strengthen the paper.
  - **Why it matters** Understanding the precise mechanism of action is important for rationalizing the selectivity and for future optimization of the compound. It also bears on the broader question of how ACTL domains mediate protein-protein interactions and whether they can be generally targeted by small molecules.
  - **Resolution test** The authors could perform additional mutational analysis of the predicted binding interface, or use techniques such as HDX-MS or NMR to map the binding site and conformational changes. Molecular dynamics simulations could also provide insight into the mechanism of disruption.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of the chemical approach
  - **Claim pointer** The authors suggest that their work "will expand the chemical and pharmacological space for bioactive compounds and open the future directions for selective perturbation of prominent ACTL-domain-containing plant bHLH TFs."
  - **Evidence pointer** Discussion
  - **Concern** The manuscript demonstrates that Stomidazolone targets MUTE, but it does not provide evidence that the approach can be generalized to other bHLH-ACTL proteins. The sequence and structural diversity of ACTL domains across the bHLH family is not discussed in detail. The claim of generalizability is speculative and not supported by data. The authors should either temper this claim or provide preliminary evidence that Stomidazolone or its analogs can affect other bHLH-ACTL proteins.
  - **Why it matters** The broader significance of the work, as stated in the Discussion, depends on the potential to target other bHLH-ACTL proteins. If the approach is specific to MUTE, the impact is more limited. Clarifying the scope of the approach is important for framing the significance.
  - **Resolution test** The authors could test Stomidazolone against a panel of bHLH-ACTL proteins in vitro, or discuss the structural conservation of the binding site across the family to support the claim of generalizability.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1e
  - **Evidence pointer** Figure 1e
  - **Issue** The quantitative analysis in Figure 1e shows stomatal and meristemoid densities, but the statistical comparisons are only indicated by letters. It would be helpful to also show the actual p-values or effect sizes in the figure or legend for readers to assess the magnitude of the effects.
  - **Required correction** Add p-values or effect sizes to the figure or legend, or provide them in the Source Data file with clear reference.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, Chemical synthesis
  - **Evidence pointer** Methods, Supplementary Data 1
  - **Issue** The chemical synthesis section is brief and refers to Supplementary Data 1 for details. While this is acceptable, the main text should include key reaction conditions (e.g., temperature, time, catalyst loading) to give readers a quick overview of the synthesis.
  - **Required correction** Add a brief summary of the key reaction conditions in the main text Methods section.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of BiFC data
  - **Affected element** Figure 6c, d
  - **Evidence pointer** Figure 6c, d
  - **Issue** The BiFC data show that Stomidazolone reduces YFP signal for SCRM-MUTE but not for SCRM-SPEC or SCRM-FAMA. However, the authors note that the effects on SCRM-SPEC were "unclear" in the text. This ambiguity should be clarified, and the statistical analysis for the BiFC data should be clearly described.
  - **Required correction** Clarify the BiFC results for SCRM-SPEC and provide clear statistical analysis for all BiFC quantifications.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Discussion of limitations
  - **Affected element** Discussion
  - **Evidence pointer** Discussion
  - **Issue** The Discussion does not address potential limitations of the study, such as the lack of a crystal structure of the MUTE ACTL domain in complex with Stomidazolone, or the potential for metabolic degradation of the compound in planta.
  - **Required correction** Add a paragraph discussing the limitations of the current study and future directions to address them.

## Risk / unsupported claims
- The claim that Stomidazolone "selectively" disrupts SCRM-MUTE heterodimers in vivo is not fully supported, as the compound also binds to other bHLH-ACTL proteins in vitro and the in vivo selectivity is inferred from phenotypic data.
- The claim that the chemical approach can be generalized to other bHLH-ACTL proteins is speculative and not supported by experimental evidence.
- The docking model of Stomidazolone binding to the MUTE ACTL domain is based on computational predictions and is not validated by a high-resolution experimental structure.
- The statement that Stomidazolone is "stable under biological conditions" is based on limited testing in specific buffers and media; long-term stability in planta is not demonstrated.

## Assessment against Nature-style criteria
- **Originality** The work is highly original. The identification of a small molecule that targets the ACTL domain of a bHLH transcription factor and disrupts its heterodimerization is a novel finding. The chemical synthesis of doubly-sulfonylated imidazolones via a new amination reaction is also an original contribution.
- **Scientific importance** The study is scientifically important. It provides a new chemical tool for studying stomatal development and demonstrates the druggability of the ACTL domain, which is a relatively understudied protein module. The work also advances our understanding of the molecular mechanisms governing stomatal lineage commitment.
- **Interdisciplinary readership** The work will appeal to a broad interdisciplinary audience, including plant biologists, chemical biologists, synthetic chemists, and structural biologists. The combination of chemistry, genetics, and biophysics makes it accessible and interesting to researchers in multiple fields.
- **Technical soundness** The technical quality of the work is high. The authors use a wide range of complementary techniques, including chemical synthesis, X-ray crystallography, ITC, BLI, Y2H, BiFC, and in vivo phenotypic analysis. The experiments are well-designed and the data are generally convincing. However, the concerns about selectivity and mechanistic detail need to be addressed.
- **Readability for nonspecialists** The manuscript is generally well-written and accessible. The introduction provides sufficient background for nonspecialists to understand the significance of stomatal development and bHLH transcription factors. The results are presented clearly, and the figures are informative. However, some sections, particularly the chemical synthesis and biophysical analysis, may be challenging for readers without a background in these areas.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a significant and novel finding with strong potential impact. The central claims are largely supported by the data, but the concerns regarding in vivo selectivity and the mechanistic detail of heterodimer disruption need to be addressed to fully establish the case. If the authors can provide additional evidence for selectivity and a more detailed mechanistic model, the manuscript would be suitable for publication in Nature Communications.