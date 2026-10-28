## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, and materials and methods
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors report that two inner membrane proteins of the pKM101 type IV secretion system, TraE and TraD, bind both single-stranded and double-stranded DNA with nanomolar affinity, that the conjugation inhibitor BAR-072 inhibits TraE DNA binding in vitro, and that conserved amino acid residues in TraE are required for conjugation
- **Visible evidence base** Abstract, Introduction, Results sections with figures referenced (Figures 1-4), Discussion, Materials and Methods, supplementary figure reference
- **Missing materials affecting confidence** Actual figure images and data plots not provided; supplementary figures not provided; raw data, statistical analyses, and experimental replicates not shown; sequence alignment details not fully visible; structural coordinates not provided

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in bacterial conjugation research by testing whether T4SS inner membrane components directly bind DNA. The biochemical approach using purified proteins with orthogonal binding assays is appropriate. However, the evidence as presented has several gaps that limit confidence in the central claims. The DNA binding data are described qualitatively without showing actual binding curves or statistical parameters. The mutagenesis data linking conserved residues to conjugation function are suggestive but do not establish a direct connection to DNA binding. The mechanism of BAR-072 inhibition is inferred without direct binding competition experiments. The relationship between the observed in vitro binding and the proposed role in DNA translocation through the T4SS remains speculative. The manuscript would benefit from additional quantitative data, controls for non-specific binding, and direct evidence linking the identified residues to DNA binding rather than general protein function.

- **Who would be interested in the results, and why** Researchers studying bacterial conjugation, type IV secretion systems, horizontal gene transfer, and antimicrobial resistance mechanisms would find these results relevant. The identification of DNA-binding activity in T4SS inner membrane components addresses a long-standing question about the DNA translocation pathway. The potential for targeting these proteins with inhibitors has therapeutic relevance for combating the spread of antibiotic resistance genes. Structural biologists studying membrane protein complexes and secretion systems may also be interested in the functional implications for T4SS architecture.

- **Major strengths** The study addresses a significant question in the field using purified proteins and orthogonal biochemical assays. The combination of EMSA and fluorescence polarization provides complementary evidence for DNA binding. The inclusion of a known conjugation inhibitor adds practical relevance. The mutagenesis approach targeting conserved residues provides a foundation for future mechanistic studies. The work builds logically on previous structural and functional characterization of TraE.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and quantification
  - **Claim pointer** The authors claim that TraE and TraD bind ssDNA and dsDNA with nanomolar affinity, with KD values of 31 nM for ssDNA and 38 nM for dsDNA for the longest oligonucleotides
  - **Evidence pointer** Results section, Figures 1C-H and 3E-H; location not provided
  - **Concern** The binding affinities are reported as specific KD values, but the actual binding curves, fit parameters, error estimates, and replicate data are not shown in the provided text. The manuscript states that experiments were performed at least three times, but no statistical analysis or variability measures are presented. The fitting model is described as "one-to-one binding" but the justification for this model and its appropriateness for a hexameric protein with potential multiple binding sites is not discussed. Without seeing the actual data and fit quality, the reported nanomolar affinities cannot be properly evaluated.
  - **Why it matters** The quantitative binding affinities are central to the claim that these proteins are part of the DNA translocation channel. If the affinities are not robustly determined, the functional significance of the binding is uncertain. The lack of error analysis and fit quality assessment prevents evaluation of whether the one-to-one model is appropriate and whether the reported KD values are reliable.
  - **Resolution test** Provide representative binding curves with fitted models, show residuals or goodness-of-fit statistics, report KD values with standard errors from at least three independent experiments, and discuss whether alternative binding models (e.g., cooperative or multi-site) were tested.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Specificity and controls
  - **Claim pointer** The authors claim that TraE and TraD specifically bind DNA, implying this is a biologically relevant property rather than non-specific electrostatic interaction
  - **Evidence pointer** Results section, Figures 1-3; location not provided
  - **Concern** The manuscript does not describe control experiments to establish binding specificity. No competition experiments with unlabeled DNA of different sequences are shown. No experiments with non-DNA polyanions (e.g., heparin, RNA) are described to rule out non-specific electrostatic interactions. Given that both proteins are positively charged membrane proteins, the observed DNA binding could reflect non-specific charge-charge interactions rather than a specific DNA-binding site. The lack of sequence specificity testing is particularly relevant since the authors claim non-specific binding but do not demonstrate this with appropriate controls.
  - **Why it matters** The biological relevance of DNA binding depends on specificity. If the binding is purely electrostatic and non-specific, it may not reflect a functional role in DNA translocation. The claim that these proteins are part of the DNA transfer pore requires evidence that the binding is specific and functionally relevant, not just a general property of positively charged proteins.
  - **Resolution test** Include competition experiments with unlabeled DNA of different sequences, test binding to RNA or other polyanions, and demonstrate that mutations that reduce DNA binding do not simply reduce overall protein positive charge. Show that DNA binding is saturable and specific.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Mechanistic link between mutagenesis and DNA binding
  - **Claim pointer** The authors claim that conserved amino acids identified by mutagenesis "may be targets for the development of more potent conjugation inhibitors" and imply these residues are involved in DNA binding
  - **Evidence pointer** Results section, Figure 4; location not provided
  - **Concern** The mutagenesis data show that mutations in conserved residues reduce conjugation efficiency, but the manuscript explicitly states that "further work is required to determine if the identified amino acids participate in DNA binding or possibly in another biological role, such as protein-protein interactions." This is an honest admission, but it means the connection between the mutagenesis results and the DNA binding claims is not established. The residues could affect conjugation through altered protein stability, membrane insertion, protein-protein interactions, or other mechanisms unrelated to DNA binding. The western blot showing comparable expression levels rules out gross stability issues but does not address proper folding or membrane insertion.
  - **Why it matters** The title and abstract imply that the identified residues are relevant to DNA binding, but the data do not support this direct connection. Overinterpreting the mutagenesis results as DNA-binding determinants could mislead future inhibitor development efforts. The therapeutic relevance of the work depends on identifying residues that are specifically important for the DNA-binding function.
  - **Resolution test** Perform DNA binding assays with the purified mutant proteins to directly test whether the mutations affect DNA binding affinity. Correlate the degree of conjugation deficiency with the degree of DNA binding impairment. If the mutations affect other properties, this should be stated explicitly and the implications for inhibitor development should be revised.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** BAR-072 mechanism of action
  - **Claim pointer** The authors claim that BAR-072 inhibits TraE DNA binding, "providing evidence for its mechanism of action"
  - **Evidence pointer** Results section, Figure 2; location not provided
  - **Concern** The inhibition experiments show that BAR-072 reduces TraE-DNA complex formation, but the mechanism of inhibition is not established. The authors previously showed that BAR-072 disrupts TraE dimerization. The current data could be explained by BAR-072 disrupting TraE oligomerization, which in turn reduces DNA binding, rather than by direct competition for the DNA binding site. The manuscript does not distinguish between competitive, non-competitive, or allosteric inhibition. The observation that inhibition has a higher impact on ssDNA than dsDNA binding is interesting but not mechanistically explained.
  - **Why it matters** Understanding the mechanism of BAR-072 inhibition is important for rational design of improved inhibitors. If the compound works by disrupting oligomerization rather than directly blocking DNA binding, different optimization strategies would be needed. The claim about "mechanism of action" is stronger than what the data support.
  - **Resolution test** Perform detailed inhibition kinetics to determine the mode of inhibition. Test whether BAR-072 competes with DNA for binding to TraE. Correlate BAR-072 effects on TraE oligomerization with effects on DNA binding using techniques like size exclusion chromatography or cross-linking.

  - **Concern ID** R1-M5
  - **Severity** Major
  - **Blocking** No
  - **Axis** Stoichiometry and oligomeric state
  - **Claim pointer** The authors discuss TraE hexameric rings and suggest DNA may translocate through the 22 Å central pore, implying the hexamer is the functional DNA-binding unit
  - **Evidence pointer** Introduction, Discussion; location not provided
  - **Concern** The manuscript does not address the stoichiometry of DNA binding to the TraE hexamer or the TraD oligomer. It is unclear whether one DNA molecule binds per hexamer, per monomer, or with some other stoichiometry. The relationship between the oligomeric state observed in previous structural studies and the DNA-binding competent state is not established. The authors mention that TraE purified in different detergents shows similar behavior, but this does not address whether the oligomeric state is the same under the binding assay conditions.
  - **Why it matters** The proposed model of DNA threading through the hexameric pore requires that the hexamer is the DNA-binding species and that the DNA binding site is accessible within the pore. Without stoichiometry data, the model remains speculative. Understanding the binding stoichiometry is also important for interpreting the KD values and for designing inhibitors.
  - **Resolution test** Determine the stoichiometry of DNA binding using techniques such as analytical ultracentrifugation, native mass spectrometry, or fluorescence-based binding assays with labeled DNA. Correlate the oligomeric state of TraE and TraD under assay conditions with DNA binding activity.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Experimental detail
  - **Affected element** EMSA methodology
  - **Evidence pointer** Materials and Methods, EMSA section; location not provided
  - **Issue** The EMSA description lacks important details such as the specific gel percentage, running conditions, and how the binding was quantified. The manuscript mentions "slower migration" but does not describe how this was measured or quantified.
  - **Required correction** Provide complete EMSA conditions including gel composition, buffer, voltage, and time. Describe how binding was quantified (e.g., densitometry) and whether the assays were performed in replicate.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 4B
  - **Evidence pointer** Results section, Figure 4B; location not provided
  - **Issue** The conjugation efficiency data are described qualitatively as "significantly reduced," "strongly reduced," or "no complementation," but no quantitative values or statistical analysis are provided. The reader cannot assess the magnitude of the effects or the variability between experiments.
  - **Required correction** Provide quantitative conjugation efficiency values with error bars and statistical tests comparing each mutant to the wild-type control. State the number of biological replicates.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Protein concentration determination
  - **Affected element** Materials and Methods, protein quantification
  - **Evidence pointer** Materials and Methods, "Protein molarity quantification and visualization"; location not provided
  - **Issue** The manuscript states that protein molar concentrations were based on hexameric TraE and pentameric TraD, but the basis for these oligomeric states under the assay conditions is not justified. If the oligomeric state varies with concentration or detergent, the reported molar concentrations and resulting KD values could be inaccurate.
  - **Required correction** Justify the use of hexameric and pentameric forms for concentration calculations, or provide evidence that these oligomeric states are stable under the experimental conditions used.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section; location not provided
  - **Issue** The discussion of the CagX DNA binding results is brief and does not provide sufficient comparison of binding affinities, specificities, or functional implications between the two systems.
  - **Required correction** Expand the comparison with CagX to include quantitative comparisons of binding properties and discuss what similarities or differences might mean for the general mechanism of DNA translocation in T4SS.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figures 1-3
  - **Evidence pointer** Results section, Figures 1-3; location not provided
  - **Issue** The manuscript references multiple panels in Figures 1-3, but the actual figures are not provided in the text. It is impossible to assess the quality of the binding curves, the completeness of the shifts, or the appropriateness of the fits.
  - **Required correction** Ensure that all figures are included with high resolution and that all panels are clearly labeled and referenced in the text.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Quantitative binding data with statistical analysis are not provided
  - R1-M2: Specificity controls for DNA binding are absent
  - R1-M3: Direct link between mutagenesis and DNA binding is not established
  - R1-M4: Mechanism of BAR-072 inhibition is not determined
  - R1-M5: Binding stoichiometry and oligomeric state under assay conditions are not established

## Risk / unsupported claims
- The claim that TraE and TraD are "DNA-binding proteins" with nanomolar affinity is not fully supported without showing the actual binding data, fit quality, and statistical analysis
- The claim that BAR-072 inhibits TraE DNA binding "providing evidence for its mechanism of action" is overstated, as the mechanism of inhibition is not established
- The claim that the identified conserved amino acids "may be targets for the development of more potent conjugation inhibitors" is speculative, as the connection between these residues and DNA binding is not demonstrated
- The proposal that DNA may translocate through the 22 Å central pore of the TraE hexamer is speculative and not directly tested in this work
- The statement that both proteins are "part of the transmembrane substrate translocation channel" is an inference not directly supported by the presented data
- The comparison with CagX DNA binding is mentioned but not quantitatively developed, making the significance of the comparison unclear