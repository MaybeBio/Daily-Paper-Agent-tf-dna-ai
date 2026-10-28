## Review setup
- **Input scope** Full manuscript text (abstract, introduction, database description, benchmarking example, conclusion)
- **Assessment boundary** Scientific content, database utility, benchmarking methodology, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors present an expansion of the Dockground resource to include protein-DNA complexes, claim it is the largest and most comprehensive dataset of its kind, describe weekly automated updates and a user-friendly web interface, and illustrate utility via an AlphaFold3 benchmarking example on 691 non-redundant structures
- **Visible evidence base** Abstract, Introduction, Database Content and Description (curation, user interface, redundancy reduction), Benchmarking Example with AlphaFold3, Conclusion, Data availability
- **Missing materials affecting confidence** Figures 1 and 2, Supplemental Figures S1 and S2, Supplemental Table S1, actual database contents and web interface functionality, detailed statistics of the dataset, AlphaFold3 benchmarking parameters and full results

## Reviewer
- **Overall assessment** The manuscript describes a valuable and timely expansion of an established structural biology resource. The addition of protein-DNA complexes to Dockground addresses a genuine need in the field, particularly given the growing importance of machine learning-based prediction of protein-nucleic acid complexes. The weekly update mechanism and user interface improvements are practical and useful. However, the manuscript as presented has several significant gaps. The claim of being the "largest, most comprehensive dataset" is not substantiated with comparative statistics against existing resources. The benchmarking example with AlphaFold3 is presented with insufficient methodological detail and the interpretation of results is somewhat superficial. The redundancy reduction methodology, while reasonable, raises questions about the balance between sequence and structural clustering approaches. Overall, the resource itself appears valuable, but the manuscript requires substantial revision to fully support its claims and provide the community with a reproducible and well-documented resource description.

- **Who would be interested in the results, and why** Computational structural biologists developing and benchmarking protein-DNA docking and prediction methods will find this resource directly useful. Researchers working on machine learning approaches for macromolecular complex prediction, particularly those using AlphaFold3 or similar tools, will benefit from the benchmark dataset. Experimental structural biologists studying protein-DNA interactions may use the resource to identify relevant complexes and contextualize their structures. The broader community interested in macromolecular recognition and interface analysis will also find value in the expanded Dockground resource.

- **Major strengths** The expansion of a well-established and widely used resource (Dockground) to include protein-DNA complexes fills a clear gap in available benchmark datasets. The weekly automated update mechanism ensures the dataset remains current, addressing a common limitation of static benchmark sets. The provision of both full and non-redundant versions at multiple sequence and structural identity thresholds provides flexibility for different use cases. The inclusion of detailed per-chain information (interface residues, buried surface area, UniProt annotations, domain information) enhances the utility of the resource for diverse analyses. The benchmarking example with AlphaFold3 demonstrates practical application and provides initial insights into the performance of state-of-the-art prediction methods on this new dataset.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** "The new Dockground protein-DNA dataset, presented in this paper, is the largest, most comprehensive dataset of protein-DNA complexes available for use for benchmarking and training of machine learning procedures."
- **Evidence pointer** Database Content and Description, Table 1 (referenced but not provided)
- **Concern** The claim of being the "largest, most comprehensive" dataset is not supported by comparative data. The manuscript does not provide statistics on the number of complexes in existing protein-DNA benchmark datasets (e.g., those referenced in [13-15]) nor does it present a direct comparison of coverage, diversity, or annotation richness against these resources. Table 1, which presumably contains the relevant statistics, is not included in the provided text.
- **Why it matters** This is a central claim of the manuscript. Without quantitative comparison to existing resources, readers cannot evaluate whether the new dataset genuinely represents an advance over current options. The claim as stated is unverifiable from the provided evidence.
- **Resolution test** Provide a table or figure comparing the number of complexes, redundancy levels, annotation completeness, and update frequency of Dockground protein-DNA against existing benchmark datasets. Clearly state the criteria used for "comprehensive" and demonstrate how Dockground meets or exceeds these criteria.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** "To illustrate the utility of the protein-DNA dataset for benchmarking, AlphaFold3 was used to generate five models (as in a standard AlphaFold3 setup) for 691 non-redundant protein-DNA structures in the Dockground database"
- **Evidence pointer** Benchmarking Example with AlphaFold3, Supplemental Table S1, Supplemental Figure S2
- **Concern** The benchmarking methodology is described at a level that prevents reproduction or independent verification. Key details are missing: the specific AlphaFold3 version used, input preparation (sequences, any templates or constraints), computational resources, runtime, and the exact criteria for the CAPRI-like classification. The results are only summarized in supplemental materials not provided. The interpretation that "AlphaFold3 modeling may yield an overall accurate structure with a less accurate or even possibly wrong interface" is presented without statistical support or comparison to other methods.
- **Why it matters** For a resource paper that aims to provide a benchmark dataset, the benchmarking example should serve as a demonstration of the dataset's utility. If the methodology is not fully described, the results cannot be reproduced or compared to other benchmarks, limiting the scientific value of the demonstration.
- **Resolution test** Provide complete methodological details for the AlphaFold3 benchmarking, including version, input formats, parameters, and computational environment. Present full results with appropriate statistical analysis, including confidence intervals and comparison to existing benchmarks or alternative methods. Ensure all supplemental tables and figures are included.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical validity
- **Claim pointer** "Two DNA chains are considered to be within the same helix if they have a greater buried surface area between them than with any other DNA chain in the structure."
- **Evidence pointer** Database Content and Description, Database curation
- **Concern** The criterion for defining a DNA double helix based on buried surface area (BSA) between chains is potentially problematic. BSA calculations can be affected by crystal packing artifacts, and the threshold for "greater BSA" is not defined. It is unclear how this criterion handles cases where a protein binds to multiple DNA duplexes, or where DNA chains have partial complementarity. The manuscript does not describe validation of this approach against known DNA duplex structures.
- **Why it matters** The correct identification of DNA duplex partners is fundamental to the definition of protein-DNA complexes in the dataset. If this criterion misassigns DNA chains, the resulting complexes and their interface annotations could be incorrect, affecting all downstream analyses and benchmarks.
- **Resolution test** Provide validation of the BSA-based helix assignment against a manually curated set of known protein-DNA complexes. Describe the BSA calculation method and any thresholds used. Discuss edge cases and how they are handled.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Resource accessibility
- **Claim pointer** "Dockground is publicly available at https://dockground.compbio.ku.edu."
- **Evidence pointer** Data availability, User interface
- **Concern** The manuscript describes the web interface and search functionality but does not provide evidence that the described features are actually implemented and functional. No screenshots, usage examples, or API documentation are provided. The URL is given but the actual content and functionality cannot be verified from the manuscript.
- **Why it matters** For a resource paper, the availability and usability of the described resource is critical. Readers need to know that the described features exist and how to use them. Without this information, the practical value of the resource cannot be assessed.
- **Resolution test** Provide screenshots of the web interface, a step-by-step usage example, and documentation of the search and download functionality. If an API is available, document its endpoints and parameters.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states the dataset is "the largest, most comprehensive" without providing any numbers or comparative context. This claim is repeated in the Introduction.
- **Required correction** Include specific numbers (e.g., total number of complexes, number of non-redundant complexes) in the abstract and temper the "most comprehensive" claim with specific criteria or comparisons.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Database curation
- **Evidence pointer** Database Content and Description, Database curation
- **Issue** The description of data extraction states "all suitable structures from CIF biounit files in the PDB were added" but does not define "suitable." The criteria for inclusion or exclusion of structures are not specified.
- **Required correction** Define the inclusion/exclusion criteria explicitly, including any filters applied (e.g., resolution, experimental method, chain length).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Benchmarking Example
- **Evidence pointer** Benchmarking Example with AlphaFold3
- **Issue** The statement "The higher percentage of incorrectly modeled interactions assessed by i-RMSD compared to those assessed by L-RMSD suggests that AlphaFold3 modeling may yield an overall accurate structure with a less accurate or even possibly wrong interface" is speculative and not supported by statistical analysis.
- **Required correction** Provide quantitative data on the distribution of scores, statistical tests comparing i-RMSD and L-RMSD distributions, and a more cautious interpretation that acknowledges alternative explanations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Redundancy reduction
- **Evidence pointer** Database Content and Description, Redundancy reduction
- **Issue** The description of structural clustering using Foldseek with TM-score thresholds is incomplete. It is unclear how the TM-score is calculated (e.g., which chains are aligned, whether DNA chains are included in the structural alignment).
- **Required correction** Clarify the structural clustering procedure, including which chains are aligned and how DNA structural similarity is assessed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Benchmarking Example
- **Evidence pointer** Benchmarking Example with AlphaFold3
- **Issue** The manuscript does not state whether the AlphaFold3 predictions and the resulting scores are available for download, which would be valuable for the community.
- **Required correction** State whether the benchmarking results are available and provide access information if they are.

## Risk / unsupported claims
- The claim that Dockground protein-DNA is the "largest, most comprehensive dataset" is unsupported without comparative statistics against existing resources.
- The AlphaFold3 benchmarking results and their interpretation are not fully assessable without the supplemental materials and complete methodological details.
- The effectiveness and usability of the web interface cannot be evaluated from the manuscript text alone.
- The BSA-based criterion for DNA helix assignment is not validated, and its accuracy is unknown.
- The statement about AlphaFold3 producing "an overall accurate structure with a less accurate or even possibly wrong interface" is speculative and not statistically supported.
- The claim of "weekly updates" is stated but the reliability and consistency of this update mechanism over time cannot be verified from the manuscript.