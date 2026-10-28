## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, supplementary data references)
- **Assessment boundary** Scientific and technical evaluation of the software module MDNA as described in the provided manuscript text; no code execution or independent benchmarking performed
- **Shared manuscript claim summary** The authors present MDNA, a Python-based software module for generating and analyzing DNA structures. The toolkit uses a spline-based mapping technique to construct DNA configurations of arbitrary shape, supports non-canonical base modifications (including Hoogsteen transitions and methylation), provides Monte Carlo minimization for structure refinement, and offers rigid body analysis tools for evaluating DNA geometries and trajectories. The authors claim this integrates structure generation and analysis into a single workflow suitable for molecular dynamics simulations.
- **Visible evidence base** Main text sections (Introduction, Materials and methods, Results and discussion, Conclusion), figure descriptions (Figs 1–3), table description (Table 1), supplementary section references (S1–S6), data availability statement
- **Missing materials affecting confidence** Supplementary sections S1–S6 and Figures S1–S3 are referenced but not provided; Table 1 contents are not shown; no code repository contents, test suite results, or benchmark data are visible; no comparison with existing tools is presented in the visible text

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful software toolkit for DNA structure generation and analysis, addressing a genuine gap in the availability of integrated, Python-native tools for constructing complex DNA geometries. The spline-based generation approach and the inclusion of non-canonical base support are interesting contributions. However, the visible evidence base is insufficient to fully evaluate the technical soundness and accuracy of the methods. Key validation data, benchmark comparisons, and detailed algorithmic descriptions are relegated to supplementary materials that were not provided for review. The claims of accuracy and utility are plausible but not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biophysics, molecular dynamics simulation, and structural biology who need to generate starting configurations for DNA-containing systems, particularly those involving DNA–protein complexes, supercoiled DNA, or modified bases. The Python-native implementation and integration with MDTraj and OpenMM would appeal to the molecular simulation community seeking scriptable, interoperable tools. The rigid body analysis module may interest researchers analyzing DNA conformational dynamics from MD trajectories.
- **Major strengths** The manuscript addresses a real gap in available tools, as existing options for generating complex DNA geometries are limited or require multiple software dependencies. The integration of generation, editing, and analysis into a single Python framework is a practical advantage. The support for non-canonical bases and base modifications (methylation, Hoogsteen) extends beyond what most existing tools offer. The use of established rigid body formalism for analysis provides a theoretically grounded approach. The case studies presented (H-NS filament, nucleosome extension, protein-mediated DNA loop) demonstrate relevant biological applications.
- **Major Concerns** The following concerns are identified from the supplied material.
- **Minor Comments** The following comments are identified from the supplied material.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The spline-based approach to DNA structure generation with integrated analysis is a novel combination, though individual components build on existing methods. Scientific importance: The tool addresses practical needs in the molecular simulation community, but the visible evidence does not yet demonstrate a significant advance over existing approaches. Interdisciplinary readership: The work is relevant to biophysics, structural biology, and computational chemistry, but the manuscript is written primarily for a specialist simulation audience. Technical soundness: The theoretical framework is based on established methods, but validation data are not visible in the supplied material. Readability for nonspecialists: The manuscript is reasonably clear for those familiar with DNA modeling, but assumes significant background knowledge; the abstract is accessible to a broader audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core concept is valuable and the software appears to address genuine needs, but the supplied material does not provide sufficient evidence to fully assess accuracy, validation, and comparative performance.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that MDNA can generate accurate DNA structures using spline-based mapping and Monte Carlo minimization, and that these structures are suitable for molecular dynamics simulations.
- **Evidence pointer** Materials and methods, Structure generation and minimization section; Figure 1; Supplementary Sections S1–S3 (not provided)
- **Concern** The accuracy of the generated DNA structures is a central claim, but no quantitative validation is presented in the visible text. The manuscript does not show comparisons of generated structures against experimental structures, crystallographic data, or established benchmarks. The root-mean-square deviation (RMSD) of generated structures from known DNA geometries, the fidelity of base pair parameters, and the energetic reasonableness of minimized structures are not reported. The supplementary sections describing the spline mapping and Monte Carlo implementation are referenced but not available for review.
- **Why it matters** Without quantitative validation, readers cannot assess whether the structures generated by MDNA are physically realistic and suitable as starting points for MD simulations. Inaccurate starting structures could lead to artifacts in downstream simulations, undermining the tool's primary purpose.
- **Resolution test** Provide quantitative validation of generated structures against known DNA geometries (e.g., RMSD from crystallographic or NMR structures for canonical B-DNA, comparison of base pair parameters with established values). Show that minimized structures have reasonable energies and that the Monte Carlo procedure converges to physically sensible configurations. Include benchmark comparisons with existing tools such as 3DNA, X3DNA, or Curves+ for equivalent generation tasks.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that MDNA provides the first native Python implementation to calculate rigid base parameters of DNA structures.
- **Evidence pointer** Materials and methods, Rigid base analysis modules section; Figure 2B and C; Supplementary Section S4 (not provided)
- **Concern** The claim of being the "first native Python implementation" is a strong assertion that requires careful verification. The visible text does not provide a comprehensive comparison with existing Python-based analysis tools or wrappers. Furthermore, the accuracy of the rigid base parameter calculations is not validated against established software such as Curves+, 3DNA, or X3DNA. The analysis shown in Figure 2B and C is described but not quantitatively compared with reference implementations.
- **Why it matters** The novelty claim is a key differentiator for the software, and the accuracy of the analysis module is critical for users who rely on these parameters for scientific conclusions. If the implementation contains subtle errors or deviates from established conventions, downstream analyses could be compromised.
- **Resolution test** Provide a systematic comparison of rigid base parameters computed by MDNA against those from Curves+ and 3DNA/X3DNA for a set of representative DNA structures and MD trajectories. Report correlation coefficients, mean differences, and any systematic deviations. Clarify the novelty claim by documenting the landscape of existing Python-based tools and their limitations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript claims that MDNA is a software module with a modular Python interface, and that the source code is publicly available via Figshare and GitHub.
- **Evidence pointer** Data availability section; Materials and methods, Overview section
- **Concern** While the data availability statement provides a DOI and mentions a GitHub repository, the visible text does not include specific version information, installation instructions, dependency requirements, or documentation of the application programming interface. The manuscript does not describe the software architecture in sufficient detail for users to understand how to extend or integrate the module. No information is provided about testing, continuous integration, or code quality assurance.
- **Why it matters** For a software contribution, reproducibility and usability are paramount. Readers need clear guidance on installation, dependencies, and basic usage to adopt the tool. The absence of these details limits the practical value of the contribution and makes it difficult for reviewers to assess the software's quality.
- **Resolution test** Provide a detailed software availability section including version number, Python version compatibility, all dependencies with versions, installation instructions, and a minimal working example. Include information about the test suite and its coverage. If possible, provide a link to the repository in the manuscript text.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that MDNA facilitates the study of DNA–protein interactions and supports new insights into DNA dynamics and molecular simulations, with case studies including H-NS filaments, nucleosome extension, and protein-mediated DNA loops.
- **Evidence pointer** Results and discussion, Building biomolecular assemblies section; Figure 3; Supplementary Section S6 (not provided)
- **Concern** The case studies are described at a qualitative level, but no quantitative results are presented. For the H-NS filament example, the manuscript does not report the quality of the generated DNA path, the energetic cost of the imposed geometry, or any validation against experimental data. For the nucleosome extension, no comparison with known nucleosome structures or linker DNA geometries is shown. The FoxP3-mediated DNA loop example lacks structural validation. The supplementary section describing these constructions is not provided.
- **Why it matters** The case studies are intended to demonstrate the tool's utility for biologically relevant systems. Without quantitative assessment, readers cannot judge whether the generated assemblies are realistic or whether the tool produces meaningful results for these applications. This weakens the case for the tool's practical value.
- **Resolution test** Provide quantitative analysis for each case study, including RMSD from reference structures where available, energetic analysis of the generated assemblies, and comparison with experimental or previously published computational models. If experimental validation is not possible, provide clear metrics for structural plausibility and discuss limitations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract mentions "Watson–Crick–Franklin" base pairing, which is an unusual terminology. The standard term in the literature is "Watson–Crick" base pairing, with the Franklin contribution acknowledged historically but not typically included in the name.
- **Required correction** Consider using the standard term "Watson–Crick" throughout the manuscript, or provide a brief justification for the extended terminology.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Structure generation and minimization section
- **Evidence pointer** Materials and methods, Structure generation and minimization section
- **Issue** The manuscript states that the writhe of the spline backbone is computed at construction time, but does not describe the method used for this computation. Different writhe calculation methods can yield different results for the same curve.
- **Required correction** Briefly describe the method used for writhe computation, or cite the specific algorithm implemented.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Sequence library and nucleotide modifications section
- **Evidence pointer** Materials and methods, Sequence library and nucleotide modifications section; Table 1
- **Issue** The manuscript states that parameters for xenogenic nucleobases are not yet available in MD force fields and suggests that general force fields such as GAFF(2) and CGenFF can be used. However, the accuracy of these general force fields for non-canonical bases is not discussed, and no guidance is provided for users on how to validate or refine these parameters.
- **Required correction** Add a brief discussion of the limitations of general force fields for modified bases and provide guidance on parameter validation or cite relevant literature.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Conclusion
- **Evidence pointer** Conclusion
- **Issue** The conclusion states that MDNA "offers insight into various dsDNA architectures" but does not specify what insights were gained in the presented case studies. This is somewhat vague.
- **Required correction** Consider either removing this claim or briefly summarizing specific insights demonstrated in the case studies.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The data availability statement mentions a Figshare DOI and a GitHub repository, but the GitHub link is not provided in the visible text.
- **Required correction** Include the full GitHub repository URL in the data availability section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Rigid base analysis modules section
- **Evidence pointer** Materials and methods, Rigid base analysis modules section
- **Issue** The manuscript states that the rigid base parameter calculation follows the theoretical framework of Curves+ and Petkevičiūtė et al., but does not specify which conventions are used for the sign conventions and reference frames. Different conventions can lead to different parameter values.
- **Required correction** Specify the exact conventions used, or state that the implementation follows the conventions of the cited references without modification.

## Risk / unsupported claims
- The claim of being the "first native Python implementation" for rigid base parameter calculation is not fully substantiated in the visible text; a comprehensive literature and software survey is needed.
- The accuracy and physical realism of generated DNA structures are asserted but not quantitatively demonstrated in the visible text.
- The suitability of generated structures as starting points for MD simulations is claimed but not validated through example MD runs or comparison with established protocols.
- The case studies are presented as demonstrations of utility, but their quality and biological relevance are not quantitatively assessed in the visible text.
- The computational cost claim ("negligible... within a minute on an everyday notebook") is not supported by benchmark data in the visible text.
- The compatibility of the non-canonical base library with existing MD force fields is discussed only superficially; the practical usability of these bases in simulations is not demonstrated.