## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, supplementary data references)
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and alignment with Nature-style criteria. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors report a method using dCas9 conjugated to quantum dots (QDs) to label specific DNA sequence classes (maxicircles, major and minor minicircles) within kinetoplast DNA (kDNA) networks from Crithidia fasciculata. They report that maxicircles are preferentially localized at the periphery of the kDNA network, that maxicircle dynamics are subdiffusive, and that peripheral maxicircle localization contributes to kDNA buckling in solution. They further report estimates of effective network stiffness from QD tracking, consistent with prior AFM-based estimates.
- **Visible evidence base** Abstract, full methods, results, discussion, figure references (Figs 1–4), supplementary figure references (S1–S13), data availability statement
- **Missing materials affecting confidence** Figures and supplementary figures not provided; raw tracking data not provided; simulation parameter files not provided; statistical details (number of replicates, error bars, significance tests) not fully specified; AFM comparison data not shown

## Reviewer

- **Overall assessment** This manuscript presents a technically interesting application of dCas9-QD labelling to a challenging biological system, the kinetoplast DNA network. The combination of experimental tracking and coarse-grained simulation is commendable and the results are potentially of interest to the biophysics and genome organization communities. However, the evidence base as provided is incomplete in several critical respects. The central claims regarding peripheral maxicircle localization, the sufficiency of this localization to cause buckling, and the stiffness estimates rest on analyses that are described but not fully visible. The statistical treatment is not reported in sufficient detail. The manuscript is promising but the case is not fully established from the supplied material.

- **Who would be interested in the results, and why** Researchers in biophysics, polymer physics, and genome organization would be interested. The kDNA is a model system for topologically complex DNA networks, and the demonstration of a method to label and track specific sequence classes within such a network is novel. The connection between sequence localization and mechanical properties (buckling, stiffness) is of broad interest. The method could also appeal to those studying bacterial genomes or other complex DNA structures.

- **Major strengths**
  1. The use of dCas9-QD as sequence-specific physical beacons in a topologically complex DNA network is a creative and potentially powerful approach.
  2. The combination of experimental tracking with coarse-grained simulations to interpret the results is a strong methodological strategy.
  3. The finding that maxicircles are peripherally localized is novel and, if robust, has implications for understanding kDNA structure and replication.
  4. The attempt to extract mechanical properties (stiffness) from dynamic tracking is valuable and connects to prior AFM work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "We discover that maxicircles display a preference to localise at the periphery of the network"
- **Evidence pointer** Results section, Fig. 2; location not provided
- **Concern** The claim of peripheral maxicircle localization is central to the paper. The description of the analysis (segmentation, boundary reconstruction, distance-to-boundary calculation, normalization by r/r0) is clear in outline, but the actual data are not visible. The figure is not provided. The number of kDNA networks analyzed (13) is stated, but the number of QD localizations per network, the criteria for including/excluding QDs, and the statistical comparison between observed and random distributions are not reported. The claim of "significant enhancement" requires a statistical test that is not described.
- **Why it matters** If the peripheral localization claim is not robustly supported, the subsequent simulation and buckling arguments lose their experimental anchor. The novelty of the paper depends on this claim.
- **Resolution test** Provide the full figure with representative images and the quantified distributions for all 13 networks. Report the statistical test used to compare observed and random distributions, including effect size and confidence intervals. State the number of QDs per network and the inclusion criteria.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "we provide evidence that the location of maxicircles at the periphery and their linking to the minicircles contributes to the buckling of kDNA in solution, as seen in experiments, and may be sufficient to cause it"
- **Evidence pointer** Results section, Fig. 3; location not provided
- **Concern** The simulation results are described qualitatively. The comparison between LB (linked border) and LD (linked diffuse) networks is stated to show that only LB networks buckle with positive mean curvature, but the quantitative data are not shown. The claim of sufficiency requires a demonstration that the observed curvature magnitude in simulations matches experimental measurements. The simulation parameters (number of independent runs, equilibration criteria, error bars on curvature) are not reported.
- **Why it matters** The buckling claim is a mechanistic hypothesis that goes beyond the experimental observations. If the simulation evidence is not quantitatively robust, the claim of sufficiency is not established.
- **Resolution test** Provide the curvature distributions for LB, LD, and MO networks, with error bars and statistical comparisons. Report the number of independent simulations. Show that the simulated curvature for LB networks quantitatively matches experimental measurements of kDNA shape.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "we can also quantify the effective network stiffness, confirming previous indirect estimations via AFM"
- **Evidence pointer** Results section, Fig. 4; location not provided
- **Concern** The stiffness estimate is derived from the plateau of g2(t) using the equipartition theorem. The value of 0.06–0.4 pN/μm is stated to be in agreement with a prior AFM estimate of 0.1 pN/μm. However, the derivation assumes a specific model (harmonic spring) that may not be valid for a topologically complex network. The uncertainty on the stiffness estimate is not reported. The comparison with AFM is qualitative and the AFM data are not shown.
- **Why it matters** The stiffness measurement is presented as a key outcome and a validation of the method. If the model assumptions are not justified or the uncertainty is large, the claim of confirmation is weakened.
- **Resolution test** Provide the full g2(t) curves with fits and residuals. Report the uncertainty on the stiffness estimate. Justify the harmonic spring model for this system. Show a quantitative comparison with the AFM estimate, including error bars on both.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "we show that dCas9 linked to quantum dots (QD) can efficiently label DNA maxicircles and different classes of DNA minicircles in kDNA"
- **Evidence pointer** Results section, Fig. 1; location not provided
- **Concern** The specificity of dCas9 binding is validated by EMSA, but the efficiency of labelling in the context of the intact kDNA network is not quantified. The number of QDs bound per kDNA, the fraction of target sites occupied, and the potential for non-specific binding or QD aggregation are not reported. The observation that PstI treatment abolishes the QD signal is supportive but does not quantify efficiency.
- **Why it matters** The method's utility depends on efficient and specific labelling. If the labelling efficiency is low or variable, the interpretation of spatial distributions and dynamics could be compromised.
- **Resolution test** Report the number of QDs detected per kDNA network, the fraction of kDNA networks showing detectable signal, and a control demonstrating that QD signal is dependent on dCas9 binding (e.g., no QD signal without dCas9 or with non-targeting sgRNA).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, simulation section
- **Evidence pointer** Materials and methods, "Molecular dynamics simulations"; location not provided
- **Issue** The description of the simulation model is brief. The bead size, spring constants, and interaction potentials are not specified. The number of minicircles (604) and maxicircles (3) is stated, but the system size and boundary conditions are not.
- **Required correction** Provide a full description of the simulation model, including all parameters, in the main text or supplementary information.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, spatial distribution analysis
- **Evidence pointer** Results section, "Maxicircles are preferentially located at the periphery"; location not provided
- **Issue** The comparison between observed and random QD distributions is described but the statistical test is not named. The statement "significant enhancement" requires a p-value or confidence interval.
- **Required correction** Report the statistical test used, the p-value or confidence interval, and the effect size.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, stiffness comparison
- **Evidence pointer** Discussion section; location not provided
- **Issue** The comparison of the measured stiffness (0.06–0.4 pN/μm) with the AFM estimate (0.1 pN/μm) is described as "excellent agreement," but the range spans a factor of ~6. The basis for this assessment is not clear.
- **Required correction** Provide a more nuanced comparison, acknowledging the range and discussing potential sources of discrepancy.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Discussion, method extension
- **Evidence pointer** Discussion section; location not provided
- **Issue** The claim that the method "could be used more broadly to quantify the static and dynamic behaviour of specific, individual genomic regions within complex genomes" is speculative. The method relies on the ability to design sgRNAs for specific sequences, which may not be feasible in all organisms.
- **Required correction** Acknowledge the limitations of the method, including the requirement for sequence-specific sgRNA design and the potential for off-target effects.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Statistical support for peripheral localization claim not reported.
  - R1-M2: Quantitative simulation data for buckling claim not shown.
  - R1-M3: Model assumptions and uncertainty for stiffness estimate not justified.
  - R1-M4: Labelling efficiency not quantified.

- **Assessment against Nature-style criteria**
  - **Originality** The application of dCas9-QD to a topologically complex DNA network is novel. The combination of experimental tracking and simulation to address a structural question is creative. The finding of peripheral maxicircle localization is new.
  - **Scientific importance** The kDNA is a model system for topologically complex DNA. Understanding the organization and dynamics of its components has implications for genome architecture and replication. The method could be transferable to other systems. The importance is moderate to high within the biophysics community.
  - **Interdisciplinary readership** The work bridges molecular biology, biophysics, and polymer physics. The methods and findings could interest researchers in these fields. The broader cell biology community may find the structural implications relevant. The interdisciplinary reach is moderate.
  - **Technical soundness** The experimental approach is sound in principle, but the evidence base is incomplete. The statistical treatment is not reported, the simulation parameters are not fully specified, and the model assumptions are not justified. The technical soundness cannot be fully assessed from the supplied material.
  - **Readability for nonspecialists** The manuscript is generally well written and the logic is clear. The abstract and introduction are accessible. The methods and results sections assume familiarity with biophysics and polymer physics concepts. The readability is acceptable for a specialist journal.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the approach is potentially powerful. However, the central claims are not fully established from the provided evidence. The authors must provide the missing statistical details, quantitative simulation data, and model justification before the case can be considered made.

## Risk / unsupported claims
- The claim of "significant enhancement" of maxicircles at the periphery is unsupported without statistical details.
- The claim that peripheral maxicircle localization is "sufficient" to cause buckling is unsupported without quantitative comparison of simulated and experimental curvature.
- The claim of "confirming previous indirect estimations via AFM" is unsupported without a quantitative comparison and uncertainty analysis.
- The claim that the method "could be used more broadly" is speculative and not supported by data.
- The statement that major and minor minicircle classes "do not display a significant enrichment" is unsupported without the same statistical treatment applied to the maxicircle analysis.