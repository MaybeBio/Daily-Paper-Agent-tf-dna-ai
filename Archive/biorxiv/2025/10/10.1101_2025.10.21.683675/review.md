## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, experimental procedures) as provided.
- **Assessment boundary** The scientific claims, methodology, data interpretation, and internal consistency of the provided manuscript text. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors identify a novel small-molecule binding groove on the ΔFOSB subunit of the AP1 transcription factor, outside the DNA-binding cleft. They report that sulfonic acid-containing compounds, particularly JPC0661, bind this groove via an induced-fit mechanism, disrupt DNA binding in vitro and in cell-based assays, and reduce ΔFOSB occupancy at genomic AP1 sites by ~60% in vivo in a mouse model of Alzheimer's disease pathology. A crystal structure of the ΔFOSB/JUND bZIP domain in complex with JPC0661 is presented to support the binding site and mechanism.
- **Visible evidence base** Abstract; Introduction; Results sections (Identifying Novel Inhibitors of ΔFOSB; JPC0661 Disrupts ΔFOSB Binding to DNA in vivo; 3D Structure of ΔFOSB/JUND bZIP+JPC0661comm; Characterization of JPC0661 Binding to ΔFOSB; Mechanism of Action of JPC0661); Discussion; Experimental Procedures (Constructs, Reagents, Protein Purification, HTS, FP Assay, EMSA, Crystallization, Structure Determination, Toxicity Assays, Microsomal Stability, In-vivo Administration, CUT&RUN Sequencing, Data Availability). Figure and table legends are referenced but not fully provided.
- **Missing materials affecting confidence** The full figures and their legends, supplementary figures and tables, and the detailed chemical synthesis schemes are not provided. This limits the ability to fully assess the quality of the structural data, the statistical significance of the CUT&RUN results, and the structure-activity relationship claims. The specific IC50 values for the analogs in cell-based assays are mentioned but not fully detailed in the text provided.

## Reviewer
- **Overall assessment** This manuscript presents a potentially significant advance in targeting a transcription factor family previously considered undruggable. The identification of a novel allosteric groove on ΔFOSB, supported by a high-resolution crystal structure and in vivo functional data, is of high interest. The work is technically ambitious, combining HTS, structural biology, and in vivo epigenomics. However, the strength of the conclusions is currently limited by the incomplete presentation of key data (figures, supplementary information) and some ambiguities in the mechanistic model. The claim of subunit selectivity requires more direct experimental support. The in vivo data, while compelling, are derived from a single model and a single readout, and the downstream functional consequences of reduced ΔFOSB occupancy are not explored. The manuscript is well-written and the rationale is clear, but the evidence base as presented is not yet fully convincing for the broadest claims.
- **Who would be interested in the results, and why** Researchers in transcription factor biology, structural biology, medicinal chemistry, and neuropharmacology. Specifically, those studying AP1 family members, FOS/JUN biology, drug addiction, Alzheimer's disease, and other conditions where ΔFOSB is implicated. The potential for a new class of small-molecule modulators for bZIP transcription factors would be of broad interest to the drug discovery community.
- **Major strengths**
    1.  The identification of a novel, potentially druggable groove on ΔFOSB outside the canonical DNA-binding interface is a significant conceptual advance.
    2.  The combination of HTS, X-ray crystallography, and in vivo CUT&RUN-sequencing provides a multi-faceted and compelling approach.
    3.  The demonstration of in vivo target engagement (reduced ΔFOSB occupancy) is a strong validation of the compound's mechanism of action.
    4.  The manuscript is clearly written and places the findings in a strong context of the challenges of targeting AP1 transcription factors.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence for mechanism of action
    - **Claim pointer** The manuscript claims that JPC0661 binding to the groove induces a conformational change that "reorients side chains critical for DNA binding" and "may hinder the ΔFOSB bZIP α-helix from binding to the major groove of DNA."
    - **Evidence pointer** Results: "3D Structure of ΔFOSB/JUND bZIP+JPC0661comm"; Figure 7
    - **Concern** The structural comparison is made between the JPC0661-bound structure and the DNA-bound structure (PDB ID: 5VPE). This is a comparison of two different states, not a direct demonstration of an allosteric mechanism. To support the claim of an induced-fit, allosteric effect, a comparison of the apo (unliganded) and JPC0661-bound structures of the same ΔFOSB/JUND bZIP construct is necessary. The text mentions a comparison with the "unliganded ΔFOSB/JUND bZIP in the reduced state" (PDB ID: 7UCC) but the details of this comparison are not provided. The conclusion that JPC0661 acts as an allosteric effector is a central claim and requires a direct structural demonstration that the compound binding causes the conformational changes, rather than merely being correlated with them in different crystal forms.
    - **Why it matters** The proposed mechanism of action is the core scientific contribution. Without a direct structural comparison of the apo and holo states, the allosteric mechanism remains speculative. The alternative explanation, that the compound simply stabilizes a pre-existing, non-DNA-binding conformation, is not excluded.
    - **Resolution test** Provide a clear, quantitative comparison of the apo (7UCC) and JPC0661-bound (9OC3) structures, including overlays and RMSD calculations for the backbone and key side chains (Lys171, Arg175, Glu178, Leu179, Arg182). Show that the conformational changes in these residues are a direct result of ligand binding and not crystal packing. If possible, perform MD simulations or provide biophysical data (e.g., HDX-MS) to support the dynamic nature of the proposed mechanism.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Support for in vivo selectivity and functional consequence
    - **Claim pointer** The manuscript claims that the druggable groove has "minimal sequence conservation across 29 bZIP domain-containing transcription factors" and suggests it can be exploited for subunit-selective compounds. It also states that JPC0661 reduces ΔFOSB occupancy at AP1 sites in vivo.
    - **Evidence pointer** Results: "JPC0661 Disrupts ΔFOSB Binding to DNA in vivo"; Figure 3; Discussion
    - **Concern** The in vivo experiment demonstrates a reduction in ΔFOSB occupancy, but it does not demonstrate selectivity. The experiment was performed in a model where ΔFOSB is highly overexpressed. It is unclear if JPC0661 also affects the occupancy of other AP1 factors (e.g., JUND, c-JUN, FOS) at the same or different sites. The claim of potential subunit selectivity is based on sequence conservation, but no functional data are presented to show that JPC0661 does not bind to or affect other bZIP family members. Furthermore, the manuscript does not report on the functional consequences of this reduced occupancy, such as changes in the expression of ΔFOSB target genes or behavioral outcomes.
    - **Why it matters** The therapeutic potential of JPC0661 hinges on its selectivity and its ability to modulate ΔFOSB function in a meaningful way. A 60% reduction in occupancy is a strong biochemical effect, but without data on selectivity and downstream gene expression, the functional relevance and potential for off-target effects remain unknown.
    - **Resolution test** Perform CUT&RUN or RNA-seq experiments to assess the genome-wide occupancy of other AP1 factors (e.g., JUND) and the transcriptomic changes in JPC0661-treated vs. vehicle-treated mice. This would demonstrate whether the effect is specific to ΔFOSB and whether it leads to changes in the expression of known ΔFOSB target genes. In vitro binding assays (e.g., FP or ITC) against other bZIP family members would also directly support the selectivity claim.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Quantitative data presentation and statistical rigor
    - **Claim pointer** The manuscript reports IC50 values for JPC0661 and its analogs in biochemical and cell-based assays, and a ~60% reduction in ΔFOSB binding peaks in vivo.
    - **Evidence pointer** Results: "Identifying Novel Inhibitors of ΔFOSB"; "JPC0661 Disrupts ΔFOSB Binding to DNA in vivo"; Figures 1, 2, 3
    - **Concern** The text provides some IC50 values (e.g., ~9 μM and ~52 μM for JPC0661comm) but does not provide the full quantitative details for all compounds and analogs in the main text. The in vivo CUT&RUN data is summarized as a percentage reduction, but the statistical significance, the number of biological replicates, and the effect size are not fully described in the text provided. The criteria for selecting the 47 candidate scaffolds from the 123 confirmed hits are described as "manually chosen," which is a potential source of bias.
    - **Why it matters** The potency and efficacy of the compounds are central to the claims. A lack of complete quantitative data and statistical details prevents a full assessment of the robustness of the findings and makes it difficult to compare the compounds' activities.
    - **Resolution test** Provide a comprehensive table of IC50 values for all compounds in all assays, with confidence intervals and the number of replicates. For the in vivo data, provide the number of animals per group, the statistical test used, and the p-values. Clarify the criteria for manual selection of scaffolds to ensure it is a systematic and unbiased process.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity of terminology
    - **Affected element** Use of "JPC0661comm" vs "JPC0661"
    - **Evidence pointer** Results: "Identifying Novel Inhibitors of ΔFOSB"
    - **Issue** The distinction between the commercially sourced compound (JPC0661comm) and the in-house synthesized compound (JPC0661) is clear but adds a layer of complexity. It is stated that they are chemically indistinguishable and similarly active, but it would be helpful to state this explicitly in the abstract or a summary figure.
    - **Required correction** Consider adding a sentence in the abstract or a footnote to clarify that JPC0661comm and JPC0661 are the same chemical entity, with the latter being a re-synthesized, purified version.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Interpretation of in vivo data
    - **Affected element** Discussion of CUT&RUN results
    - **Evidence pointer** Results: "JPC0661 Disrupts ΔFOSB Binding to DNA in vivo"
    - **Issue** The manuscript states that JPC0661 treatment "causes a robust, broad reduction in ΔFOSB binding across most this transcription factor’s normal genomic locations." The gene ontology analysis suggests a potential selective effect on genes involved in proteasomal regulation. This is an interesting observation, but the text is somewhat speculative about the implications.
    - **Required correction** Clarify whether the GO analysis was performed on the genes that lost ΔFOSB binding or on the genes that retained binding. This distinction is crucial for interpreting the potential functional consequences.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Experimental detail
    - **Affected element** In vivo compound administration
    - **Evidence pointer** Experimental Procedures: "In-vivo JPC0661 Compound Administration"
    - **Issue** The concentration of JPC0661 delivered (50 μM) and the rate (16.7 ng/h) are provided, but the rationale for this dose is not given. It is also unclear if this dose is expected to achieve a relevant concentration in the brain tissue.
    - **Required correction** Briefly state the rationale for the chosen dose, perhaps referencing preliminary PK studies or solubility limits.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Structural data quality
    - **Affected element** Crystallographic statistics
    - **Evidence pointer** Results: "3D Structure of ΔFOSB/JUND bZIP+JPC0661comm"; Table 1
    - **Issue** The text mentions "relatively high Rwork and Rfree values" due to anisotropic diffraction. While this is acknowledged, it is a concern for the overall quality of the structural model.
    - **Required correction** In the main text, provide a brief statement on the resolution limits and the overall quality of the electron density for the ligand, to reassure the reader that the ligand placement is unambiguous.

## Risk / unsupported claims
- The claim that the identified groove can be exploited to develop "AP1-subunit-selective compounds" is a reasonable hypothesis based on sequence analysis, but it is not directly supported by functional data showing selectivity.
- The statement that JPC0661 "may hinder the ΔFOSB bZIP α-helix from binding to the major groove of DNA" is presented as a possible mechanism but is not definitively proven by the structural data, which is a static snapshot.
- The claim that the compound acts as an "allosteric effector" is not fully supported without a direct comparison of apo and holo structures.
- The functional consequences of the ~60% reduction in ΔFOSB occupancy in vivo are not assessed, so the claim that this represents a therapeutically relevant modulation is not yet established.
- The manuscript states that JPC0661 is "an inhibitor of ΔFOSB-mediated transcription in cell-based assays," but the data for this is not shown in the provided text, only referenced.