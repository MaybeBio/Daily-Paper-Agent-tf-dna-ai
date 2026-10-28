## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a crystal structure of the p73 DNA binding domain (DBD) in complex with a 12-bp DNA sequence and molecular dynamics simulations with six p53 natural promoter sequences. They propose that sequence-specific DNA structural features, particularly at positions 3, 8, 13, and 18, are recognized by p73 residues Lys138 and Arg268, and that these interactions influence p73 tetramerization and transactivation function.
- **Visible evidence base** Abstract text only; no structural coordinates, statistics, simulation parameters, or functional assays are provided
- **Missing materials affecting confidence** Full methods, crystallographic data and refinement statistics, MD simulation protocols and convergence analyses, functional transactivation data, sequence alignment details, and any validation of the proposed mechanism

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting structural and computational study addressing p73 DNA recognition specificity. However, the claims regarding mechanism, tetramerization, and functional consequences are not adequately supported by the evidence visible in the abstract. The study may be of interest to the transcription factor and p53 family research community, but the current presentation does not establish the central conclusions.
- **Who would be interested in the results, and why** Researchers studying p53 family transcription factors, DNA recognition mechanisms, protein-DNA interactions, and transcriptional regulation. The structural data on p73 DBD-DNA complexes could inform understanding of how p73 achieves promoter selectivity, which is relevant to cancer biology and developmental gene regulation.
- **Major strengths** The study addresses a biologically important question regarding how p73 distinguishes between different response elements. The combination of crystallography and molecular dynamics is appropriate for investigating protein-DNA recognition. The identification of specific residues (Lys138 and Arg268) and DNA positions provides a testable hypothesis.
- **Major Concerns** The abstract claims a mechanistic link between DNA sequence, p73 tetramerization, and transactivation function, but the evidence for this link is not visible. The crystal structure is of a 12-bp DNA, while the natural response elements are 20-bp, and the abstract does not explain how the shorter construct relates to the full-length RE. The claim that "each 20-base pair natural promoter forms a different major/minor groove" is presented without supporting structural or simulation data. The functional relevance of the proposed tetramerization differences is asserted but not demonstrated.
- **Minor Comments** The abstract uses the term "promiscuous nature" without defining the specific selectivity problem being addressed. The relationship between the 12-bp crystallized sequence and the six natural promoter sequences used in simulations is unclear. The abstract does not specify the p73 isoform or domain boundaries used in the crystallographic construct.
- **Technical failings that need to be addressed before the case is established** The abstract does not provide crystallographic resolution, R-factors, or validation metrics. No simulation timescales, force fields, or convergence criteria are given. No functional data linking the proposed structural differences to transactivation are presented.
- **Assessment against Nature-style criteria** Originality: The question of p73 RE selectivity is not new, but the specific structural insights may be novel; however, this cannot be fully assessed from the abstract. Scientific importance: Potentially high for the transcription factor field, but the abstract does not establish the broader significance beyond the p53 family. Interdisciplinary readership: The abstract is likely accessible to structural biologists and molecular biologists, but the mechanistic claims require more evidence to attract a wider audience. Technical soundness: Cannot be evaluated from the abstract alone; the lack of methodological detail is a concern. Readability for nonspecialists: The abstract is reasonably clear but uses field-specific terminology without sufficient context.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible hypothesis but does not provide sufficient data to support the central mechanistic claims. A full manuscript with structural validation, simulation details, and functional assays would be required to assess the case.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that "the loops L1 and L3 bearing these residues influence inter-and intra-dimer interfaces interactions and hence p73 forms a unique tetramer with each natural promoter sequence."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The claim that p73 forms a unique tetramer with each natural promoter sequence is presented as a conclusion, but no structural or biophysical evidence for tetramer formation is visible in the abstract. The crystal structure is of a DBD-DNA complex, which may not capture tetrameric assembly. The MD simulations are mentioned but no details on how tetramerization was assessed are provided.
- **Why it matters** Tetramerization is central to p53 family function, and the claim that DNA sequence dictates distinct tetramer conformations is a strong mechanistic statement. Without direct evidence, this claim cannot be evaluated and may overinterpret the available data.
- **Resolution test** Provide explicit structural or biochemical data demonstrating tetramer formation for each promoter sequence, such as crystallographic or SAXS data, or quantitative binding assays showing cooperative assembly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The abstract states that "Structural features of the DNA and the spacing between half-sites influence p73 tetramerization and its transactivation function."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract links DNA structural features and half-site spacing to transactivation function, but no functional data are presented. The crystal structure uses a 12-bp DNA, which does not include the full 20-bp RE or the spacer region. The MD simulations use six natural promoters, but the abstract does not describe how transactivation was measured or correlated with the structural observations.
- **Why it matters** The claim establishes a direct structure-function relationship that is central to the paper's significance. Without functional validation, the structural observations remain correlative and the mechanistic conclusion is unsupported.
- **Resolution test** Include transactivation assays (e.g., reporter gene assays) for the six promoters and demonstrate that differences in tetramerization or DNA structure correlate with functional output.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Construct relevance
- **Claim pointer** The abstract reports "the crystal structure of p73 DNA binding domain (DBD) in complex with 12 base pair DNA sequence 5'-cAGGCATGCCTg-3'."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The crystallized DNA is 12-bp, while the natural response elements are 20-bp with a spacer of 0 to 13 bp. The abstract does not explain how the 12-bp construct represents a half-site or how the missing spacer and second half-site affect the interpretation. The sequence shown contains only one half-site motif, and the relevance to full-length RE recognition is unclear.
- **Why it matters** The structural basis for recognizing full-length REs is the stated goal, but the crystallographic construct may not capture the relevant interactions. If the structure only represents a half-site, the conclusions about full RE recognition and tetramerization may be overextended.
- **Resolution test** Clarify the relationship between the 12-bp construct and the full 20-bp RE, or provide additional structures or models of full-length RE complexes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Background description
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that p73 activates "more than 50% of cell fate p53 target genes" but does not define what "cell fate" genes are or how this percentage was determined.
- **Required correction** Provide a reference or clarify the basis for this percentage, or rephrase to avoid an unsubstantiated quantitative claim.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Sequence motif description
- **Evidence pointer** Abstract text; location not provided
- **Issue** The motif "(PPPC-A/T-T/A-GYYY)" is presented without explanation of the notation, and the use of hyphens and slashes may be confusing to nonspecialist readers.
- **Required correction** Define the notation clearly, for example by stating that P represents purines and Y represents pyrimidines, and explain the variable positions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Simulation description
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions "molecular dynamics simulations with six different p53 natural promoter sequences" but provides no information on simulation length, force field, or analysis methods.
- **Required correction** Include brief methodological details in the abstract or refer to the methods section for these parameters.

## Risk / unsupported claims
- The claim that p73 forms a unique tetramer with each natural promoter sequence is unsupported by visible evidence.
- The claim that DNA structural features and half-site spacing influence transactivation function is unsupported by visible functional data.
- The claim that "each 20-base pair natural promoter forms a different major/minor groove" is presented without supporting structural or computational evidence.
- The relevance of the 12-bp crystal structure to full-length 20-bp response element recognition is not established.
- The percentage of p53 target genes activated by p73 ("more than 50%") is stated without reference or methodological basis.