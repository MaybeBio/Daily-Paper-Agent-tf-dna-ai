## Review setup
- **Input scope** Full manuscript text (main text, methods, figure legends referenced but not provided in full)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and conclusions as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors propose that PCNA acts as a nucleotide exchange factor (NEF) for the RFC clamp loader ATPase complex, accelerating ADP release from specific RFC subunits to biologically relevant timescales. This claim is supported by cryo-EM structures of apo RFC, biochemical nucleotide exchange assays, and molecular dynamics simulations.
- **Visible evidence base** Cryo-EM reconstructions (six 3D classes, 2.5–2.7 Å resolution), MANT-ATP fluorescence binding assays, equilibrium MD simulations (2 μs × 3 replicates), τ-RAMD dissociation simulations (120 total), dynamical network analysis
- **Missing materials affecting confidence** Full figures and supplementary figures not provided; exact quantitative data from biochemical assays (rate constants, error bars, replicates) not fully described; MD simulation convergence metrics not shown; τ-RAMD methodology details incomplete; statistical analysis details for biochemical experiments not provided

## Reviewer

- **Overall assessment** This manuscript presents a compelling and novel hypothesis: that PCNA, the substrate of the RFC clamp loader, functions as a nucleotide exchange factor to accelerate ADP release. The combination of cryo-EM, biochemistry, and MD simulations is appropriate and potentially powerful. However, the evidence as presented has several gaps that need to be addressed before the central claim is fully established. The cryo-EM structures are used to infer ADP release rates indirectly, the biochemical data are described qualitatively without clear quantitative rigor, and the MD simulations, while suggestive, require more careful validation to support the strong conclusions drawn.

- **Who would be interested in the results, and why** Researchers studying DNA replication and repair mechanisms, particularly those focused on clamp loaders and sliding clamps. The broader AAA+ ATPase community will also find interest given the proposed analogy to GTPase regulatory mechanisms. The conceptual framework of a substrate acting as its own NEF may have implications for other ATP-driven molecular machines.

- **Major strengths** The study addresses a fundamental gap in understanding the clamp loading mechanism: how ADP release is coordinated with PCNA binding. The multi-technique approach is well-suited to the question. The cryo-EM structures of apo RFC with mixed nucleotide occupancy provide novel insights into the dynamic nature of the complex. The MD simulations offer mechanistic hypotheses that are testable. The analogy to GTPase/GEF systems is intellectually stimulating and may have broad relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central claim
- **Claim pointer** "PCNA is a nucleotide exchange factor for the clamp loader ATPase complex" and "PCNA accelerates nucleotide exchange at the slowly exchanging subunit(s) from hours to within the dead time of mixing"
- **Evidence pointer** Figure 5, MANT-ATP fluorescence assays section
- **Concern** The central biochemical claim that PCNA accelerates ADP release is based on MANT-ATP binding assays, but the data are presented only qualitatively. The manuscript states that fluorescence increases "within the dead time of mixing" when PCNA is present, but no quantitative rate constants, amplitudes, or statistical comparisons are provided. The interpretation that the slow phase represents ADP release from C and D subunits is inferred from the cryo-EM structures, but this correlation is not directly tested. Furthermore, the assay measures MANT-ATP binding, not ADP release directly, and the relationship between these processes needs clarification.
- **Why it matters** The central claim of the paper rests on this biochemical evidence. Without quantitative data showing that PCNA specifically accelerates ADP release from the C and D subunits, the conclusion that PCNA is a NEF is not fully supported. The current presentation does not allow the reader to assess the magnitude of the effect or its statistical significance.
- **Resolution test** Provide quantitative analysis of MANT-ATP binding kinetics with and without PCNA, including rate constants, amplitudes, and statistical comparisons across replicates. Ideally, directly measure ADP release using radiolabeled or fluorescent ADP. Show that the effect is specific to PCNA and not a general protein effect.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural interpretation
- **Claim pointer** "The AAA+ module of the A subunit is flexibly tethered to the core of the RFC complex" and "the D and C subunits are active ATPase sites and ATP hydrolysis at these sites is required for efficient clamp loading"
- **Evidence pointer** Figure 1, Figure 2, cryo-EM section
- **Concern** The cryo-EM structures show no density for the A subunit AAA+ domain, which is interpreted as flexibility. However, the possibility that this domain is simply disordered or partially degraded cannot be excluded without additional validation. The mixed nucleotide occupancy (GDP in E, ADP in C and D, none in B) is used to infer relative ADP release rates, but the authors do not discuss whether the sample preparation or grid freezing conditions could bias nucleotide occupancy. The correlation between observed occupancy and release rates is an assumption that needs justification.
- **Why it matters** The structural observations are used to support the model that C and D release ADP slowly. If the occupancy patterns are influenced by experimental artifacts, the model would be weakened. The interpretation of the A subunit flexibility is also important for understanding the mechanism.
- **Resolution test** Perform additional validation of the A subunit flexibility, such as SEC-MALS or cross-linking mass spectrometry. Discuss and rule out potential artifacts in nucleotide occupancy. If possible, determine structures with defined nucleotide states to directly compare.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** MD simulation validity
- **Claim pointer** "MD Simulations Predict Fast ADP Release from the A and B Subunits and Slow ADP Release from the C and D Subunits" and "MD Simulations Predict That PCNA Promotes Nucleotide Exchange in RFC by Opening the D-E Interface"
- **Evidence pointer** Figure 4, Figure 6, MD simulation sections
- **Concern** The τ-RAMD simulations are used to predict relative ADP release rates, but the methodology is not described in sufficient detail. The manuscript states that "the calculated dissociation times are not physically realistic" yet uses them to draw conclusions about relative rates. The equilibrium MD simulations show only one trajectory (out of five) where the D subunit engages PCNA and releases ADP. The statistical significance of this single event is unclear. The dynamical network analysis is used to identify communication hubs, but the relationship between betweenness centrality and functional importance is not validated experimentally.
- **Why it matters** The MD simulations provide mechanistic support for the proposed model. If the simulations are not robust or the analysis is not statistically sound, the mechanistic conclusions are weakened. The single trajectory showing ADP release is particularly concerning.
- **Resolution test** Provide more detailed τ-RAMD methodology, including convergence criteria and error estimates. Show that the observed ADP release in the D subunit is reproducible across multiple independent simulations. Validate the network analysis predictions with mutational experiments.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Alternative explanations
- **Claim pointer** "PCNA is a NEF for RFC" and "we propose that this mechanism helps ensure that RFC binds PCNA before DNA"
- **Evidence pointer** Discussion section
- **Concern** The authors propose that PCNA acting as a NEF ensures ordered binding of PCNA before DNA. However, alternative explanations for the observed acceleration of nucleotide exchange are not fully explored. For example, PCNA binding could induce a conformational change that indirectly affects the nucleotide binding sites, rather than acting as a true exchange factor. The distinction between a specific NEF mechanism and a more general allosteric effect is not addressed. Additionally, the physiological relevance of the proposed ordering mechanism is speculative and not directly tested.
- **Why it matters** The proposed mechanism has implications for understanding clamp loading regulation. If the effect is indirect, the analogy to GTPase GEFs may be misleading. The physiological significance of the proposed ordering is important for the broader impact of the work.
- **Resolution test** Perform experiments to distinguish between a specific NEF mechanism and a general allosteric effect, such as testing PCNA mutants that bind but do not induce conformational changes. Test the proposed ordering mechanism in a more physiological context, such as with full-length RFC and PCNA on DNA.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 3
- **Evidence pointer** Figure 3A-C
- **Issue** The description of the structural alignments in Figure 3 is confusing. The text states that "subunits were aligned about their active sites" but the RMSD values are reported for both "aligned residues" and "overall Cα RMSD of the AAA+ module." The distinction between these two measurements is not clear.
- **Required correction** Clarify the alignment procedure and clearly define what is meant by "aligned residues" versus "overall Cα RMSD." Consider showing the alignment in a supplementary figure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods
- **Evidence pointer** MANT-ATP fluorescence assays section
- **Issue** The methods for the MANT-ATP fluorescence assays are incomplete. The concentrations of RFC, PCNA, and MANT-ATP are not specified, and the buffer conditions are not fully described. The dead time of mixing is mentioned but not quantified.
- **Required correction** Provide complete experimental details, including all concentrations, buffer compositions, and the dead time of the stopped-flow or manual mixing apparatus.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section, analogy to GTPases
- **Issue** The analogy to GTPase GEFs is interesting but may be overstated. GTPase GEFs are dedicated regulatory proteins, whereas PCNA is a substrate that also serves as an exchange factor. The authors should acknowledge this distinction and discuss whether the analogy is truly apt or primarily heuristic.
- **Required correction** Soften the analogy and explicitly discuss the differences between dedicated GEFs and the proposed substrate-mediated exchange mechanism.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 7
- **Evidence pointer** Figure 7, Discussion
- **Issue** The model presented in Figure 7 is described in the text but the figure itself is not shown. The description of the model is somewhat speculative, particularly regarding the ordering of PCNA binding before DNA binding.
- **Required correction** Ensure the figure is clear and that the speculative aspects of the model are clearly labeled as such.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion section, connection to other clamp loaders
- **Issue** The discussion of alternative clamp loaders is brief and does not fully address how the proposed NEF mechanism might apply to these systems. For example, do CTF18-RFC and Rad24-RFC also use their respective sliding clamps as NEFs?
- **Required correction** Expand the discussion to address the potential generality of the proposed mechanism across clamp loader systems.

## Risk / unsupported claims
- The claim that PCNA accelerates ADP release "from hours to within the dead time of mixing" is not quantitatively supported by the data presented.
- The inference that the A subunit AAA+ domain is "flexibly tethered" based solely on missing density in cryo-EM maps is not fully validated.
- The prediction that PCNA promotes nucleotide exchange by opening the D-E interface is based on a single MD trajectory and requires more robust statistical support.
- The proposal that the NEF mechanism ensures ordered binding of PCNA before DNA is speculative and not directly tested.
- The analogy to GTPase GEFs, while heuristic, is not fully justified given the differences between dedicated regulatory factors and substrate-mediated exchange.
- The claim that "PCNA is a NEF for RFC" is presented as a definitive conclusion, but the evidence, while suggestive, does not fully exclude alternative mechanisms.