## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodological soundness, and interpretation of results as presented in the provided manuscript
- **Shared manuscript claim summary** The authors investigate how tethering the leucine zipper (ZIP) and forkhead (FKH) domains of the human transcription factor FoxP1 via a ~90-residue disordered linker impacts dimerization, conformational stability, and DNA-mediated allostery. Using replica-exchange discrete molecular dynamics (rxDMD) simulations, ensemble and single-molecule fluorescence spectroscopy, and chemical denaturation, they report that: (1) domain tethering promotes dimerization primarily through ZIP coiled-coil interactions while inhibiting FKH 3D domain-swapping; (2) tethering increases the thermodynamic stability of both domains; (3) the linker mediates open and closed conformational states; and (4) DNA binding allosterically modulates domain dynamics and decreases dimerization propensity.
- **Visible evidence base** Main text figures (Figs. 2, 3, 4, 5), supplementary tables (Tables S1–S5), supplementary figures (Figs. S1, S2, S4), methods section, data analysis section
- **Missing materials affecting confidence** Supplementary figures S3 and S5 are referenced but not provided; raw simulation trajectories and analysis scripts are not provided; experimental replicates and error analysis details are partially described but not fully documented; the DNA sequence used in binding experiments is not specified in the main text

## Reviewer

- **Overall assessment** The manuscript addresses a timely and important question in transcription factor biology: how domain tethering via disordered linkers modulates dimerization and allostery in a multidomain protein. The combination of atomistic simulations with ensemble and single-molecule fluorescence approaches is commendable and appropriate for the question. The central claims are partially supported by the presented evidence, but several technical concerns regarding data analysis, model assumptions, and interpretation of single-molecule anisotropy data need to be resolved before the conclusions can be fully accepted. The finding that DNA binding decreases dimerization propensity via allosteric interdomain communication is potentially significant but requires stronger experimental validation.
- **Who would be interested in the results, and why** Researchers studying transcription factor regulation, particularly the FoxP subfamily; investigators interested in the role of disordered linkers in multidomain protein function; biophysicists using single-molecule fluorescence to study protein conformational dynamics; computational biologists using coarse-grained or discrete molecular dynamics to explore protein energy landscapes. The results may also be relevant to those studying allosteric regulation in dimeric transcription factors more broadly.
- **Major strengths** The study combines complementary computational and experimental approaches to address a mechanistically important question. The use of single-molecule fluorescence anisotropy to probe domain-specific dynamics is technically sophisticated. The thermodynamic analysis of domain stability in the context of tethering provides quantitative insight. The observation that DNA binding differentially affects the two domains and reduces dimerization propensity is a novel finding with potential functional implications.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of single-molecule anisotropy interpretation
- **Claim pointer** The authors claim that DNA binding causes "local changes in both ZIP and FKH domains" and that the two populations observed in the 2D anisotropy-lifetime histograms represent open and closed conformational states.
- **Evidence pointer** Fig. 5(b), Fig. 5(c), Tables S3–S5, section "Single-molecule anisotropy analysis"
- **Concern** The interpretation of the two populations in the 2D histograms as open and closed states relies on the assumption that changes in rotational correlation time directly report on interdomain contacts. However, the BODIPY label is attached via a flexible linker to a cysteine residue, and its rotational freedom can be affected by local dynamics, dye-protein interactions, or changes in the local environment upon DNA binding that are unrelated to global conformational changes. The authors do not adequately control for these possibilities. Additionally, the assignment of the slow rotational correlation time to a "closed" state and the fast component to an "open" state is not independently validated by the simulations. The rxDMD simulations predict open and closed states, but the connection between simulated ensembles and the experimentally observed anisotropy populations is not quantitatively established.
- **Why it matters** The central claim of DNA-mediated allostery between the ZIP and FKH domains rests on the interpretation of these single-molecule anisotropy data. If the observed changes in anisotropy are due to local dye dynamics or other artifacts rather than genuine interdomain conformational changes, the allostery conclusion would be substantially weakened.
- **Resolution test** The authors should provide independent validation of the open/closed state assignment, for example by performing anisotropy measurements with labels at multiple positions, using a rigid dye with restricted motion, or correlating the anisotropy populations with FRET measurements that directly report on interdomain distances. Alternatively, they could use the simulation trajectories to compute predicted anisotropy values for the open and closed states and compare these quantitatively with the experimental distributions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Thermodynamic model validity
- **Claim pointer** The authors report unfolding free energies (GU) of 10 ± 0.5 kcal/mol for the ZIP-lin dimer, 12 ± 0.4 kcal/mol for the ZIP domain in the ZIP-lin-FKH dimer, and 12 ± 0.6 and 6 ± 0.1 kcal/mol for the two transitions of the FKH domain in the ZIP-lin-FKH dimer.
- **Evidence pointer** Fig. 3(a), Fig. 3(b), Tables S2–S3, section "Equilibrium unfolding"
- **Concern** The analysis of the unfolding data relies on the assumption of specific unfolding models (two-state for ZIP-lin, three-state for ZIP-lin-FKH). However, the choice of model appears to be made post hoc based on the shape of the curves rather than being rigorously tested against alternative models. For example, the claim that the FKH domain unfolds via a three-state mechanism in the context of the full construct is based on the observation of two transitions, but the authors do not demonstrate that a two-state model is statistically inadequate. Furthermore, the GU values are derived from fitting to equations that assume linear dependence of free energy on denaturant concentration, which may not hold over the full range of denaturant concentrations used. The error bars reported are fitting errors and do not account for systematic uncertainties in the model choice.
- **Why it matters** The quantitative thermodynamic parameters are central to the claim that tethering stabilizes both domains. If the model assumptions are incorrect, the reported GU values and the conclusions about stabilization would be unreliable.
- **Resolution test** The authors should perform rigorous model comparison (e.g., using F-tests or Akaike information criterion) to justify the choice of two-state versus three-state models. They should also report the m-values and demonstrate that the linear extrapolation model is valid over the denaturant range used. Ideally, they would use multiple complementary techniques (e.g., circular dichroism, size exclusion chromatography at different denaturant concentrations) to validate the unfolding mechanism.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Simulation methodology and validation
- **Claim pointer** The authors state that rxDMD simulations predict "closed and open states with and without interdomain contacts" and that the linker "mediates the mutual organization and dynamics of ZIP and FKH domains."
- **Evidence pointer** Fig. 4, section "Replica-exchange discrete molecular dynamics (DMD) simulations"
- **Concern** The rxDMD simulations use a coarse-grained force field (Medusa with CHARMM19-based energy function) and implicit solvent. While this approach is appropriate for exploring conformational landscapes, the authors do not validate the simulation results against experimental data beyond qualitative comparisons. The representative structures shown in Fig. 4 are selected from basins in the PMF, but the criteria for selecting these structures are somewhat arbitrary. More importantly, the simulations are performed on monomeric constructs, yet the experimental findings relate to dimeric states. The connection between the simulated monomeric open/closed states and the experimentally observed dimeric behavior is not clearly established.
- **Why it matters** The simulations provide the structural interpretation for the experimental observations. If the simulated ensembles do not accurately represent the relevant conformational states, the proposed mechanism of interdomain communication would lack structural support.
- **Resolution test** The authors should validate the simulations by comparing predicted observables (e.g., radius of gyration, secondary structure content, interdomain distances) with experimental measurements where possible. They should also discuss how the monomeric simulations relate to the dimeric state and whether the open/closed states observed in the monomer are expected to persist in the dimer.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of the allosteric effect
- **Claim pointer** The authors conclude that "DNA allosterically promotes structural changes that decrease the dimerization propensity of FoxP1" and postulate that this is "crucial for the gene regulatory function of FoxP1."
- **Evidence pointer** Fig. 5, section "DNA-mediated structural allostery between the ZIP and FKH domains modulates dimerization"
- **Concern** The functional significance of the observed decrease in dimerization propensity upon DNA binding is speculative. The authors do not demonstrate that this effect occurs in a cellular context or that it has consequences for transcriptional regulation. The DNA concentration used in the dimerization assay (10 nM) is not clearly justified, and the physiological relevance of the observed 2-fold change in KD is unclear. Additionally, the authors do not test whether the effect is specific to the cognate DNA sequence or whether non-specific DNA would produce similar effects.
- **Why it matters** The claim that DNA binding regulates dimerization is presented as a key finding with functional implications. Without evidence that this effect is biologically relevant, the significance of the finding is diminished.
- **Resolution test** The authors should test the effect of non-specific DNA on dimerization, perform experiments at physiologically relevant DNA concentrations, and ideally demonstrate functional consequences in a cellular or in vitro transcription assay.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of experimental conditions
- **Affected element** Dimerization assay conditions
- **Evidence pointer** Fig. 2, section "Dimerization, DNA-binding, and unfolding experiments"
- **Issue** The buffer conditions for the dimerization assays are not fully specified. The authors mention "standard buffer" but do not define its composition in the main text. Additionally, the temperature at which the dimerization titrations were performed is stated as 37 °C, but it is unclear whether the unfolding experiments were also performed at this temperature.
- **Required correction** Provide the full composition of the standard buffer in the main text or refer to a specific supplementary section. Clearly state the temperature for all experiments.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Error reporting
- **Evidence pointer** Tables S1–S5, Fig. 3
- **Issue** The errors reported for KD and GU values appear to be standard errors from fitting, but the number of independent replicates is not clearly stated. For single-molecule experiments, the number of molecules analyzed and the number of independent measurements should be reported.
- **Required correction** Clearly state the number of independent replicates for each experiment and the number of molecules analyzed in single-molecule experiments. Report the appropriate statistical measures (e.g., standard deviation, confidence intervals).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality and completeness
- **Affected element** Fig. 2(d)
- **Evidence pointer** Fig. 2(d)
- **Issue** The comparison between the FRET efficiency histograms of the isolated FKH domain and the ZIP-lin-FKH construct is difficult to evaluate because the two panels are not directly overlaid. The authors state that the dimeric state of ZIP-lin-FKH "does not form a 3D-DS dimer," but the quantitative comparison between the two conditions is not shown.
- **Required correction** Provide an overlay of the two histograms or a quantitative comparison (e.g., mean FRET efficiency and distribution width) to support the claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Domain tethering"
- **Evidence pointer** Throughout the manuscript
- **Issue** The term "domain tethering" is used to describe the covalent linkage of the ZIP and FKH domains via the disordered linker. However, this term could be confused with other uses in the literature (e.g., membrane tethering). A brief definition at first use would improve clarity.
- **Required correction** Define "domain tethering" at first use and consider using a more specific term such as "linker-mediated tethering" or "covalent domain linkage."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The authors do not explicitly discuss the limitations of their approach, such as the use of a coarse-grained force field in simulations, the potential artifacts of fluorescent labeling, or the simplified two-state model for dimerization.
- **Required correction** Add a paragraph in the Discussion acknowledging the limitations of the methods and how they might affect the interpretation of the results.

- **Technical failings that need to be addressed before the case is established** R1-M1 (single-molecule anisotropy interpretation), R1-M2 (thermodynamic model validity), R1-M3 (simulation validation)

- **Assessment against Nature-style criteria**
  - **Originality** The study addresses a question that has not been systematically explored in the FoxP family: how the disordered linker between ZIP and FKH domains modulates their coupled behavior. The finding that DNA binding allosterically decreases dimerization propensity is novel. However, the general concept of linker-mediated interdomain communication in multidomain proteins is well established, and the specific novelty here is incremental rather than paradigm-shifting.
  - **Scientific importance** The FoxP transcription factors are clinically important, and understanding the molecular basis of their regulation has potential implications for disease mechanisms. However, the study is primarily biophysical in nature, and the direct link to biological function is not established. The importance is moderate and would be enhanced by demonstrating functional consequences of the observed allosteric effects.
  - **Interdisciplinary readership** The work bridges computational biophysics, single-molecule fluorescence, and protein biophysics. It would appeal to researchers in these fields, as well as to those studying transcription factor regulation. However, the specialized nature of the methods and the focus on a single protein system may limit broader appeal.
  - **Technical soundness** The combination of methods is appropriate, and the experimental design is generally sound. However, the concerns raised above regarding the interpretation of single-molecule anisotropy data and the validity of the thermodynamic models need to be addressed. The lack of rigorous model comparison and independent validation of the open/closed state assignment weakens the technical foundation.
  - **Readability for nonspecialists** The manuscript is generally well-written and the logic is clear. However, the methods section and data analysis are highly technical and may be challenging for readers without a strong biophysics background. The figures are informative but some (particularly Fig. 5) require careful study to interpret.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an interesting and potentially important question, and the combination of methods is appropriate. However, the central claims regarding DNA-mediated allostery and the quantitative thermodynamic parameters require stronger validation. The authors should address the concerns about the interpretation of single-molecule anisotropy data, rigorously justify their thermodynamic models, and provide additional validation of the simulation results. If these issues are resolved, the manuscript would make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that DNA binding "decreases the dimerization propensity of FoxP1" is based on a single experimental condition (10 nM DNA) and a 2-fold change in KD. The physiological relevance of this effect is not established.
- The assignment of the two populations in the single-molecule anisotropy histograms to "open" and "closed" states is not independently validated and may be an oversimplification.
- The claim that tethering "inhibits a FKH domain-swapped structure" is based on FRET experiments that show low FRET efficiency, but the authors do not rule out alternative explanations (e.g., different dimer geometry, dye orientation effects).
- The extrapolation of simulation results from monomeric constructs to the dimeric state is not justified.
- The statement that "the linker mediates the mutual organization and dynamics of ZIP and FKH domains" is supported by simulations but not directly by experiments.
- The claim that "FoxP1 in cells will be in its dimeric form" is speculative and not supported by any in vivo or cellular data.