## Review setup

- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, and claims as presented in the provided text; no external data or supplementary files were available for review
- **Shared manuscript claim summary** The authors report quantitative DNA binding affinities for three BRCA1 domains (DBD1, DBD2, BRCT) against three DNA substrates (ssDNA, dsDNA, G4) using biolayer interferometry, and propose functional specialization whereby DBD1 directs BRCA1 to double-strand breaks for homologous recombination while DBD2 and BRCT recognize non-canonical structures at telomeres and replication forks
- **Visible evidence base** Figures 1-6 (described in text), Tables 1-3 (referenced), circular dichroism data (referenced as Supporting Information, not provided)
- **Missing materials affecting confidence** Raw BLI sensorgrams, full binding curves with replicates, CD spectroscopy data, protein purity gels with molecular weight markers, DNA substrate sequences beyond descriptions, statistical analysis details, structural model generation parameters

## Reviewer

- **Overall assessment** This manuscript presents a straightforward biophysical characterization of three BRCA1 domains binding to three DNA substrates. The experimental approach is appropriate and the data, as described, appear internally consistent. However, the central claims extend substantially beyond what the data can support. The authors propose a functional model of BRCA1 domain specialization in homologous recombination and telomere maintenance based solely on equilibrium binding constants measured in isolation. The affinity differences reported are modest (within approximately 2-fold for DBD1 across substrates; approximately 1.4-fold for DBD2 between G4 and ssDNA), and the manuscript does not address whether these differences are statistically significant or biologically meaningful. The structural model presented in Figure 6 is described qualitatively without methodological detail. The manuscript would benefit from either tempering the functional claims or providing additional evidence linking the observed binding preferences to in vivo function.

- **Who would be interested in the results, and why** Researchers studying BRCA1 biochemistry and function, particularly those interested in DNA repair pathway choice, homologous recombination mechanisms, and telomere biology. The quantitative binding data for isolated BRCA1 domains may also be of interest to structural biologists and biophysicists studying protein-DNA interactions. Clinically oriented researchers studying BRCA1 variants of unknown significance may find the framework useful, though the authors do not test any pathogenic variants.

- **Major strengths** The manuscript addresses a gap in quantitative understanding of BRCA1 domain-specific DNA binding. The use of biolayer interferometry with a 1:1 binding model is methodologically sound for measuring equilibrium constants. The inclusion of three distinct DNA substrates relevant to BRCA1 biology is thoughtful. The authors appropriately acknowledge prior work and position their findings within the existing literature. The writing is clear and accessible.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claims exceed evidence
- **Claim pointer** "These findings support a model in which DBD1 directs BRCA1 to DSB sites to facilitate DNA end resection during HR, whereas DBD2 and BRCT contribute to the role of BRCA1 in telomere maintenance and chromatin remodeling through the recognition of non-canonical DNA structures."
- **Evidence pointer** Results section, Figures 3-5, Table 3
- **Concern** The functional model proposed in the abstract, discussion, and conclusions is not supported by the experimental data presented. The authors measured equilibrium binding constants of isolated domains to purified DNA substrates in vitro. They did not test whether these domains function in homologous recombination, telomere maintenance, or chromatin remodeling. The affinity differences between substrates for each domain are modest. For DBD1, the K values are 2.92 x 10^7 M^-1 for dsDNA versus 1.67 x 10^7 M^-1 for ssDNA and 1.52 x 10^7 M^-1 for G4, representing less than 2-fold differences. For DBD2, the difference between G4 and dsDNA is approximately 1.4-fold. The authors do not report statistical significance for these differences, and the 95% confidence intervals overlap substantially based on the reported errors. A model of functional specialization requires demonstration that these affinity differences translate to differential recruitment or activity in a biological context, or at minimum, that the differences are statistically robust and biologically meaningful.
- **Why it matters** The central thesis of the manuscript is that BRCA1 domains are functionally specialized for different DNA repair pathways. If the binding preferences are not statistically significant or are too small to be biologically relevant, the functional model collapses. The manuscript currently presents a descriptive biophysical characterization but claims a mechanistic model.
- **Resolution test** The authors should either (1) provide statistical analysis demonstrating that the affinity differences between substrates are significant, (2) temper the functional claims to match the descriptive nature of the data, or (3) provide additional evidence linking the binding preferences to function, such as competition assays, mutagenesis of key residues, or cellular assays with domain-specific mutants.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical methodology incomplete
- **Claim pointer** "BLI binding isotherms were constructed by plotting the steady-state response (Δλ) values against protein concentration. The curves were fit to a 1:1 binding model in Scientist 3.0 software"
- **Evidence pointer** Materials and Methods, Data analysis; Results, Biolayer interferometry assays
- **Concern** The methods section lacks critical details necessary to evaluate the quality and validity of the binding measurements. The authors do not report the concentration ranges tested for each protein-substrate pair, the number of concentrations used, whether the protein concentrations bracketed the expected K values, or how the 1:1 binding model was validated. The manuscript states that measurements were performed in triplicates on separate days, but does not report the variability between independent experiments versus within-experiment replicates. The authors reference a prior publication for "further methodological details," but the provided information is insufficient for a reader to assess whether the BLI experiments were properly designed and executed. Additionally, the authors state that branched DNA substrates were excluded "to maintain 1:1 binding stoichiometry," which is an assumption that should be tested rather than assumed.
- **Why it matters** The quantitative binding constants are the sole experimental output of this manuscript. If the methodology is not fully described and validated, the reliability of all reported values is uncertain. The 1:1 binding model assumption is particularly important because if the actual stoichiometry differs, the reported K values would be incorrect.
- **Resolution test** The authors should provide complete methodological details including concentration ranges, number of data points, validation of the 1:1 model (e.g., through residuals analysis or comparison with alternative models), and a more complete description of how replicates were handled in the analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural model not substantiated
- **Claim pointer** "As shown in Figure 6, DBD1 and DBD2 are predicted to occupy opposite, solvent-accessible surfaces of BRCA1, consistent with functional specialization."
- **Evidence pointer** Discussion, Figure 6
- **Concern** The structural model presented in Figure 6 is described qualitatively without any methodological information. The authors do not state what structural data or prediction algorithms were used to generate the model, whether it is based on experimental structures, homology models, or ab initio predictions, or what the confidence level of the prediction is. The interpretation that DBD1 and DBD2 occupy "opposite, solvent-accessible surfaces" and that this "is consistent with functional specialization" is speculative. The claim that BRCT is "positioned internally within the full-length BRCA1 model" and therefore "will have less access to the DNA" is an interpretation that requires validation.
- **Why it matters** The structural model is used to support the functional specialization hypothesis. If the model is not reliable or the interpretation is not validated, this line of argument is weakened. The manuscript does not provide sufficient information for readers to evaluate the quality of the structural predictions.
- **Resolution test** The authors should describe the source of the structural model, the methods used to generate it, and any validation performed. Alternatively, the structural discussion could be removed or substantially tempered if the model is not experimentally validated.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance not established
- **Claim pointer** "DBD2's preference for G4 DNA is consistent with previous reports linking BRCA1 to the resolution of replication stress and telomeric structures, where G4 DNA commonly form."
- **Evidence pointer** Discussion, Results, DNA binding profiles
- **Concern** The authors use a single G4 substrate derived from human telomeric repeat sequences to represent all G4 structures. G4 structures are highly polymorphic, with different loop lengths, sequences, and topologies. The authors do not test whether the observed binding is specific to the telomeric G4 or generalizes to other G4 structures. Furthermore, the connection between in vitro G4 binding and telomere maintenance is correlational. The authors do not demonstrate that the G4 binding activity of DBD2 or BRCT is required for telomere function, nor do they test whether mutations that disrupt G4 binding affect telomere maintenance.
- **Why it matters** The claim that DBD2 and BRCT contribute to telomere maintenance through G4 recognition requires evidence that G4 binding is functionally relevant. A single in vitro binding measurement to one G4 sequence is insufficient to establish this connection.
- **Resolution test** The authors should either test additional G4 substrates with different sequences and topologies, perform mutagenesis to identify residues required for G4 binding and test their functional consequences, or temper the claims about telomere maintenance to reflect the correlational nature of the evidence.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and Methods, Buffers and reagents
- **Evidence pointer** "Buffer G" referenced in Results but "Buffer H" defined in Methods
- **Issue** The Results section refers to "Buffer G" in the BLI workflow description, but the Materials and Methods section defines "Buffer H" as the experimental buffer. This inconsistency is confusing.
- **Required correction** Clarify whether Buffer G and Buffer H are the same buffer, or correct the nomenclature to be consistent throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, Expression and purification
- **Evidence pointer** Figure 1
- **Issue** The authors state that proteins were purified to "near homogeneity" and migrated as single bands, but no purity percentage or quantification is provided. The molecular weight markers are not described.
- **Required correction** Provide a brief description of the estimated purity and include molecular weight markers in the figure or legend.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, DNA binding profiles
- **Evidence pointer** Table 3
- **Issue** The reported K values include 95% confidence intervals, but the authors do not report whether the differences between substrates for each domain are statistically significant. Given the overlapping confidence intervals apparent from the reported values, this is an important omission.
- **Required correction** Provide statistical comparisons between substrates for each domain, or explicitly state that no statistical comparisons were performed.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 1
- **Issue** The authors state that "the 1:1 stoichiometry observed in our BLI experiments supports a model in which these domains engage with DNA substrates directly and independently." However, the 1:1 stoichiometry was an assumption used in the fitting model, not an independently observed result.
- **Required correction** Revise this statement to accurately reflect that 1:1 stoichiometry was assumed in the analysis, not experimentally determined.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and Methods, DNA oligos
- **Evidence pointer** Table 2
- **Issue** The DNA substrate sequences are referenced in Table 2 but not provided in the text. The G4 substrate is described as "formed from the human telomeric repeat sequence" but the specific sequence and folding conditions are not described.
- **Required correction** Provide the full sequences of all DNA substrates and describe the G4 folding protocol.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, Biolayer interferometry assays
- **Evidence pointer** Figure 2
- **Issue** The description of the BLI workflow in the Results section is overly detailed and duplicates information that belongs in the Methods. The figure legend is not provided in the text.
- **Required correction** Streamline the Results description and ensure the figure legend contains the necessary experimental details.

## Risk / unsupported claims

- The functional model of BRCA1 domain specialization in homologous recombination and telomere maintenance is not supported by the in vitro binding data alone. The affinity differences between substrates are modest and no statistical significance is reported.
- The claim that DBD1 "directs BRCA1 to DSB sites to facilitate DNA end resection" is speculative. No functional assays were performed to test this.
- The claim that DBD2 and BRCT "contribute to the role of BRCA1 in telomere maintenance and chromatin remodeling" is speculative. No cellular or biochemical assays linking these domains to telomere function were performed.
- The structural interpretation in Figure 6 is not substantiated. The source and generation method of the structural model are not described.
- The statement that "the 1:1 stoichiometry observed in our BLI experiments" is misleading, as 1:1 stoichiometry was assumed in the fitting model, not experimentally verified.
- The biological relevance of the measured binding affinities is not established. The authors do not compare their measured K values to any functional threshold or to concentrations of these DNA structures present in cells.
- The claim that "BRCT's interactions with this substrate further suggests BRCA1's involvement in telomeric surveillance" is an overinterpretation of a single in vitro binding measurement.