## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, evidence quality, and claims as presented in the supplied text; no supplementary files, figures, or tables were available for inspection
- **Shared manuscript claim summary** The authors combine ProtT5 protein language model embeddings with network analysis to construct a multiscale representation of 121,673 non-redundant protein binding sites, showing that embedding-derived networks capture ligand-associated organization, resolve recognition microenvironments within individual kinases, and identify local similarities across evolutionarily distant proteins
- **Visible evidence base** Main text narrative with references to Supplementary Figures SF1–SF7, Supplementary Tables ST1–ST2, and Supplementary Material SM1; none of these supplementary items were provided for review
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; specific numerical results beyond those quoted in text; methodological details for ProBiS comparisons, DIAMOND clustering, and Infomap analysis; code availability statement

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting framework for organizing protein binding-site diversity using protein language model embeddings and network science. The multiscale perspective, from local neighborhoods to mesoscopic communities to cross-category similarities, is well articulated and the focus on interpretability of embedding space is timely. However, the evidence base available for review is incomplete, with all figures and supplementary materials absent. The central claims regarding structural relevance, ligand-associated organization, and the biological meaning of detected communities rest on analyses that cannot be independently evaluated from the supplied text. The manuscript is well written and the conceptual framing is clear, but the technical validation and quantitative support for several key claims are not assessable in their current form.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, binding-site characterization, and representation learning would find this framework relevant. Researchers in drug discovery, particularly those interested in polypharmacology, off-target prediction, and repurposing, may also find the cross-protein similarity networks useful for hypothesis generation. The work bridges protein language models and network medicine, an area of growing interest.

- **Major strengths** The conceptual framing of binding-site space as a multiscale network is clear and compelling. The use of experimentally defined ligand-contacting residues rather than full-protein embeddings is a thoughtful choice that grounds the representation in functional biology. The explicit attention to interpretability, including the distinction between geometric diversity and community compaction, shows methodological care. The kinase case study is well motivated given the pharmacological importance of this family. The authors are appropriately cautious in several places, acknowledging that embedding similarity does not establish pharmacological cross-reactivity and that conformational states are not resolved.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The claim that "embedding proximity was associated with local structural similarity, supporting the structural relevance of network relationships" is central to the entire framework
- **Evidence pointer** Supplementary Figure SF4; location not provided
- **Concern** The structural calibration analysis using ProBiS is described only in a single paragraph. The sampling strategy, the distribution of ProBiS Z-scores across embedding distance bins, the choice of threshold, and the statistical significance of the observed trend are not reported in the text. Without access to SF4 or quantitative summary statistics, the strength of the association between embedding similarity and structural similarity cannot be evaluated.
- **Why it matters** This calibration is the foundational evidence that the embedding space carries structural information relevant to binding sites. If this association is weak or driven by trivial factors such as sequence identity, all downstream network interpretations are compromised.
- **Resolution test** Provide the full ProBiS comparison results, including correlation coefficients, confidence intervals, and the proportion of pairs exceeding the Z-score threshold as a function of embedding distance. Show that the association holds after controlling for sequence identity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The claim that "communities within individual proteins distinguished separate binding regions and resolved recurrent residue-defined microenvironments within broad structural classes" is presented as a key result
- **Evidence pointer** Figure 2, Supplementary Figure SF5, Supplementary Table ST2; location not provided
- **Concern** The quantitative support for this claim is not visible. The text reports weighted purity of 0.984 and homogeneity of 0.828 averaged across eight kinases, with a permutation-based p-value for purity, but the per-kinase breakdown, the definition of the null model, and the interpretation of the homogeneity-completeness tradeoff are not provided. The specific case of p38α is described qualitatively, but the correspondence between communities and structural classes is not shown.
- **Why it matters** The claim that network communities resolve biologically meaningful microenvironments is the main interpretative contribution of the kinase analysis. Without per-kinase statistics and visual or quantitative evidence of the community-structure correspondence, the claim remains anecdotal.
- **Resolution test** Provide per-kinase purity, homogeneity, completeness, and AMI values with confidence intervals. Show the confusion structure between communities and structural classes for at least one representative kinase. Demonstrate that the observed subdivision is not an artifact of the Louvain resolution parameter.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The claim that "local similarities also connected sites in proteins with low sequence identity and non-overlapping InterPro annotations, suggesting shared recognition features across distant proteins" is presented as evidence of cross-category organization
- **Evidence pointer** Supplementary Figure SF7, Supplementary Material SM1; location not provided
- **Concern** The filtered network contained 1,823 nodes and 1,904 edges, which is a very sparse subgraph. The text describes three components qualitatively, but no quantitative assessment of whether this connectivity exceeds what would be expected by chance is provided. The possibility that these connections reflect shared cofactor chemistry or generic physicochemical properties rather than specific recognition features is acknowledged but not tested.
- **Why it matters** The claim of shared recognition features across distant proteins is the most speculative and potentially impactful result. If the connectivity is not statistically enriched relative to a suitable null model, the claim reduces to anecdotal observation.
- **Resolution test** Provide a statistical test comparing the observed cross-protein connectivity to a null model that preserves degree distributions and ligand chemistry. Report enrichment of specific ligand features or physicochemical properties within connected components.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The methods for graph construction, community detection, and diversity quantification are described at a high level but lack critical details
- **Evidence pointer** Materials and Methods section; location not provided
- **Concern** The choice of k = 30 for the mutual nearest-neighbor graph is justified only by the size of the largest connected component. The PCA reduction to 300 components is mentioned but the variance explained is approximate. The normalization procedure for cosine similarity is not specified. The Infomap parameters and the Louvain resolution are not reported. The definition of the null model for the permutation test is not given.
- **Why it matters** Network analyses are sensitive to construction choices. Without these details, the robustness of the reported organization cannot be assessed, and the work cannot be reproduced.
- **Resolution test** Provide full parameter specifications, sensitivity analyses for k and PCA dimensionality, and a reproducibility statement with code availability.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive caution
- **Claim pointer** The discussion states that "the observed association between embedding similarity and ProBiS structural similarity therefore provides an important empirical basis for interpreting this representation"
- **Evidence pointer** Discussion section; location not provided
- **Concern** The authors acknowledge that pooled embeddings do not encode spatial arrangement of residues or ligand chemistry. However, the extent to which the ProBiS association is driven by sequence context rather than local structural features is not quantified. The possibility that the embedding captures protein family information rather than binding-site-specific features is raised but not addressed with control analyses.
- **Why it matters** If the embedding similarity largely reflects host-protein identity, the cross-protein connections and community structure may be trivial consequences of sequence similarity rather than convergent binding-site features.
- **Resolution test** Perform a control analysis where embeddings are compared after removing the contribution of sequence identity, or where the ProBiS association is stratified by sequence identity bins.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, embedding generation
- **Evidence pointer** Materials and Methods, "Binding site embeddings and network construction"; location not provided
- **Issue** The description of how ligand-contacting residues are defined and mapped to the receptor sequence is incomplete. The handling of gaps, insertions, and multiple chains is not described.
- **Required correction** Provide a precise description of residue selection criteria, sequence alignment procedure, and handling of missing or ambiguous residues.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, structural calibration
- **Evidence pointer** Results, "Structural calibration and a nonredundant binding site atlas"; location not provided
- **Issue** The text states that ProBiS Z-scores greater than 2 were treated as evidence of significant structural similarity, but the number of comparisons, the false discovery rate, and the sensitivity of the conclusions to this threshold are not reported.
- **Required correction** Report the number of comparisons, the distribution of Z-scores, and a sensitivity analysis for the threshold choice.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Methods, diversity metrics
- **Evidence pointer** Materials and Methods, "Embedding diversity and community compaction"; location not provided
- **Concern** The definitions of G div and C geom are given but the interpretation of "geometric diversity" as a percentile-based measure is not intuitive. The relationship between these metrics and standard diversity measures is not discussed.
- **Required correction** Clarify the interpretation of these metrics and relate them to existing diversity or entropy measures in the literature.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, cross-protein connectivity
- **Evidence pointer** Results, "Local binding site similarity across globally distant proteins"; location not provided
- **Issue** The three described components are presented as illustrative, but the criteria for selecting these components and the total number of components with similar properties are not given.
- **Required correction** Report the distribution of component sizes and the fraction of components that contain cross-family connections.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, software and data
- **Evidence pointer** Materials and Methods, "Data source"; location not provided
- **Issue** No code availability statement, software versions, or computational resource details are provided.
- **Required correction** Add a data and code availability statement with software versions and parameters.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, limitations
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion of limitations is thorough but does not address the potential impact of embedding context window on binding-site representation. ProtT5 embeddings are sequence-contextual, and the effective context may vary across protein lengths.
- **Required correction** Add a brief discussion of how sequence context length might affect the representation of binding sites in proteins of different sizes.

## Risk / unsupported claims
- The claim that embedding proximity is associated with local structural similarity is not quantitatively supported in the visible text; the supporting figure (SF4) was not provided
- The claim that communities resolve "recurrent residue-defined microenvironments" within kinases is not supported by per-kinase statistics in the visible text
- The claim that cross-protein connections suggest "shared recognition features" is presented without statistical enrichment analysis
- The statement that "the network exhibited ligand-related organization" is supported only by the assortativity value of 0.72, with no confidence intervals or comparison to null expectations
- The claim that "these results show how network organization captures both diversification within protein categories and local similarities across their boundaries" is an interpretive synthesis that extends beyond the directly demonstrated results
- The four "recurrent modes of BS organization" described in the results are presented as robust patterns, but the stability of these modes across parameter choices is not demonstrated
- The statement that "the observed association between embedding similarity and ProBiS structural similarity therefore provides an important empirical basis for interpreting this representation" overstates the strength of evidence given the incomplete reporting of the calibration analysis