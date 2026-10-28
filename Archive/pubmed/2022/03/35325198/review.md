## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Structural biology claims, methodological validity, and biological relevance of higher-order G-quadruplex models
- **Shared manuscript claim summary** The authors present an integrative structural biology (ISB) approach combining CD, AUC, SAXS, and MD simulations to determine solution structures of long (34–70 nt) wild-type promoter sequences from c-Myc, c-Kit, and k-Ras. They report five structures: three forming two stacked G-quadruplex units, one forming three stacked units, and one forming a quadruplex-hairpin structure. They also introduce quantitative CD for counting stacked G-tetrads and DNaseI cleavage for hairpin detection.
- **Visible evidence base** Abstract, full introduction, methods, results, discussion, conclusion, data availability statement
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S29), SAXS data files, MD trajectory details, NMR spectra referenced as Supplementary Figure S28, and structural coordinate files

## Reviewer
- **Overall assessment** This manuscript presents a technically ambitious and potentially valuable application of integrative structural biology to a challenging class of nucleic acid systems. The combination of multiple biophysical techniques to derive models of higher-order G-quadruplex assemblies is commendable and addresses a genuine gap in the field. However, the central claim that these models are "self-consistent" and structurally reliable is not fully established from the evidence presented. The resolution of the approach (18 Å) is acknowledged, but the interpretation of some data, particularly the quantitative CD calibration and the handling of conformational heterogeneity, requires more rigorous justification. The biological significance of the proposed structures remains largely speculative. The manuscript would benefit from clearer presentation of model validation metrics and a more critical discussion of the limitations of the approach.
- **Who would be interested in the results, and why** Researchers in nucleic acid structural biology, particularly those studying G-quadruplexes in promoter regions; scientists interested in integrative structural biology methodologies; drug discovery groups targeting G-quadruplexes in oncogene promoters. The methodological advances in quantitative CD and the demonstration of ISB for complex nucleic acid systems would be of broad interest.
- **Major strengths**
  1. Addresses a significant and technically challenging problem: structural characterization of long, native promoter sequences that form higher-order G-quadruplex assemblies.
  2. The integrative approach, combining multiple orthogonal biophysical techniques, is methodologically sound in principle and represents a valuable strategy for systems intractable to high-resolution methods.
  3. The validation of CRYSOL Rg calculations against experimental SAXS data for a library of known G-quadruplex structures provides a useful benchmark for the field.
  4. The identification of unique interfacial regions and druggable sites in the models offers potentially novel insights for drug discovery.
  5. The work is clearly presented and the logic of the ISB workflow is well explained.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "The formal resolution of our approach is 18 angstroms, but in some cases structural features of only a few nucleotides can be discerned."
  - **Evidence pointer** Results section, Figure 6, Table 3
  - **Concern** The claim that structural features of only a few nucleotides can be discerned at a formal resolution of 18 Å is not adequately supported. At this resolution, distinguishing specific loop conformations or interfacial contacts between G-quadruplex units is extremely challenging. The authors do not provide a clear metric for how this "discernment" is achieved or validated. The models are presented as if they have predictive power at the nucleotide level, but the resolution of the experimental data does not appear to justify this.
  - **Why it matters** This claim is central to the paper's contribution. If the models cannot reliably resolve features at the nucleotide level, then the proposed druggable sites and structural details are not reliable. Overstating the resolution of the approach undermines the credibility of the structural models.
  - **Resolution test** The authors should provide a clear, quantitative demonstration of the resolution limits of their approach. This could include: (a) a systematic analysis of how well the models reproduce known structural features in the control structures (e.g., 1XAV); (b) a discussion of the uncertainty in loop conformations and how this propagates to the proposed druggable sites; (c) a comparison of models generated from different starting conditions to demonstrate convergence.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "We confirmed that the magnitude of the normalized CD signal at 264 nm for parallel promoters is proportional to the number of stacked G4s."
  - **Evidence pointer** Results section, Figure 2
  - **Concern** The quantitative CD calibration relies on a linear relationship established using d[TGnT]4 tetramers. The authors then apply this calibration to intramolecular, higher-order structures with potentially different electronic environments, loop geometries, and stacking interactions. The validity of this extrapolation is not adequately justified. The presence of non-G-quadruplex elements (e.g., hairpins in c-Kit-12) and the potential for different stacking geometries could significantly alter the CD response per tetrad.
  - **Why it matters** The number of stacked G-tetrads is a key constraint used in model building. If the CD calibration is inaccurate for these complex systems, the resulting models will be built on incorrect constraints, potentially leading to wrong structures.
  - **Resolution test** The authors should validate the CD calibration on a system where the number of stacked tetrads is known independently (e.g., a well-characterized higher-order G-quadruplex structure). They should also discuss the potential effects of loop composition and geometry on the CD signal and provide error estimates for the tetrad counts derived from CD.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "The k-Ras-8 model exemplifies this point... its poor fit to its scattering data (e.g. skewing in its P(r) and Kratky profiles and poor χ2 fit) indicates that a population of structurally distinct isomers likely co-exist."
  - **Evidence pointer** Results section, Figure 5, Figure 6
  - **Concern** The authors acknowledge that the k-Ras-8 model has a poor fit to the SAXS data (χ2 = 5.6) and attribute this to conformational heterogeneity. However, they do not attempt to model this heterogeneity or provide any estimate of the relative populations of different isomers. The presented model is therefore not a satisfactory representation of the solution state. The same issue may apply to other models where the fit is better but still not perfect.
  - **Why it matters** A model that does not fit the experimental data is not a valid structural model. The authors' admission of heterogeneity without attempting to characterize it leaves the k-Ras-8 structure essentially unvalidated. This undermines the claim that the ISB approach can "satisfactorily characterize" complex systems.
  - **Resolution test** The authors should either: (a) perform a rigorous ensemble analysis (e.g., using programs like EOM or BILBOMD) to model the conformational heterogeneity and provide population estimates; or (b) present the k-Ras-8 model as a preliminary hypothesis with clear caveats, rather than a validated structure.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "Each structure exhibits interfacial regions between stacked quadruplexes or novel loop geometries that are possible druggable targets."
  - **Evidence pointer** Discussion section, Figure 10
  - **Concern** The biological relevance of the proposed druggable sites is not demonstrated. The SiteMap druggability scores are presented as evidence of potential drug targeting, but no experimental validation is provided. The scores for the higher-order structures (0.87–1.00) are only modestly higher than those for the monomeric G-quadruplex (0.55–0.69), and the significance of this difference is not discussed. More importantly, the claim that these sites are "possible druggable targets" is speculative without any demonstration that ligand binding at these sites has a functional consequence.
  - **Why it matters** The paper's significance partly rests on the claim that these structures offer new opportunities for drug discovery. Without experimental evidence of druggability or functional relevance, this claim is not supported.
  - **Resolution test** The authors should either provide experimental evidence of ligand binding to the proposed sites (e.g., by SPR, ITC, or NMR) or temper their claims about druggability. A more detailed discussion of the limitations of computational druggability predictions would also be appropriate.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability for nonspecialists
  - **Affected element** Introduction
  - **Evidence pointer** Introduction section
  - **Issue** The introduction assumes significant prior knowledge of G-quadruplex structure and nomenclature. Terms like "G-register exchange," "propeller loops," and "spare tire hypothesis" are used without adequate explanation for a general structural biology audience.
  - **Required correction** Provide brief definitions or explanations for these specialized terms, or add a short primer on G-quadruplex structural features for nonspecialist readers.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods
  - **Evidence pointer** Materials and Methods, Molecular modeling section
  - **Issue** The description of the MD simulation protocol is incomplete. The force field parameters for the G-quadruplexes, the ion parameters, the equilibration protocol, and the criteria for determining when a model is "stable" are not fully described. The use of "accelerated molecular dynamics" is mentioned but not explained.
  - **Required correction** Provide a more detailed description of the MD protocol, including software versions, force field parameters, ion conditions, simulation length, and convergence criteria. A reference to a more detailed methods description would be acceptable.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Results
  - **Evidence pointer** Results section, "Validation of CRYSOL Rg calculations" subsection
  - **Issue** The validation of the CRYSOL approach uses a library of 14 G-quadruplex structures, but the criteria for selecting these structures are not stated. It is unclear whether these represent a diverse enough set to validate the approach for the higher-order structures studied here.
  - **Required correction** State the selection criteria for the validation set and discuss whether the set adequately represents the structural diversity of the higher-order G-quadruplexes studied.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of biological relevance is largely speculative. The connection between the proposed structures and transcriptional regulation is not developed beyond general statements.
  - **Required correction** Either provide a more focused discussion of how the specific structural features identified could impact transcription factor binding or other regulatory mechanisms, or clearly state that the biological implications are currently unknown.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Results
  - **Evidence pointer** Results section, Figure 5
  - **Issue** The correlation between calculated and experimental Rg values is presented as strong (r² = 0.9855), but the plot appears to include both the calibration set and the higher-order structures. It would be clearer to separate the validation of the method from its application to the new structures.
  - **Required correction** Present the validation of the CRYSOL method on known structures separately from the application to the new higher-order structures, to avoid any appearance of circularity.

## Risk / unsupported claims
- The claim that "structural features of only a few nucleotides can be discerned" at 18 Å resolution is not quantitatively supported.
- The extrapolation of the quantitative CD calibration from simple tetrameric systems to complex higher-order structures is not adequately validated.
- The k-Ras-8 model is presented as a structure despite the acknowledged poor fit to SAXS data, without a rigorous treatment of conformational heterogeneity.
- The biological relevance and druggability of the proposed interfacial regions are speculative and not experimentally supported.
- The claim that "higher-order quadruplex assemblies may be a common feature within the genome" is an extrapolation from a small number of sequences and is not supported by the data presented.
- The methodological advance of "quantitative CD for counting stacked G-tetrads" is not fully established as a general method, given the limited validation on complex systems.