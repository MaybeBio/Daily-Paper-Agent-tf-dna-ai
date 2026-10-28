## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report a new class of chromatin contact patterns, termed "chromatin jets," observed in quiescent mammalian lymphocytes, and propose that these jets are landmarks of cohesin-driven loop extrusion. They claim that narrow origins of loop extrusion favor jet formation, that jets propagate symmetrically for 1-2 Mb in the absence of CTCF constraints, and that asymmetric CTCF binding deflects jet propagation, indicating a switch from bidirectional to unidirectional loop extrusion with independent directional control.
- **Visible evidence base** Abstract text only; no experimental data, polymer simulation details, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, polymer simulation methodology, experimental protocols, quantitative analyses, and any statistical validation

## Reviewer

- **Overall assessment** The abstract presents a conceptually interesting and potentially significant observation regarding cohesin-mediated loop extrusion, with a novel descriptive term ("chromatin jets") and a plausible mechanistic interpretation. However, the abstract alone provides insufficient evidence to evaluate the robustness of the claims. The central assertions regarding jet formation, propagation range, and directional switching rest on experimental and computational evidence that is not visible in the supplied material. The work may be of interest to the chromatin biology and genome organization communities, but the case is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers in chromatin architecture, genome organization, and gene regulation would be interested, as the findings potentially refine current models of cohesin-driven loop extrusion and its regulation by CTCF. Computational biologists studying polymer models of chromosome folding may also find the simulation-based claims relevant. The work could inform broader understanding of 3D genome organization in quiescent versus active cell states.
- **Major strengths** The abstract introduces a clearly defined and visually evocative concept ("chromatin jets") that may provide a useful framework for interpreting Hi-C contact patterns. The claim that asymmetric CTCF binding can deflect jet propagation offers a testable prediction linking directional loop extrusion to CTCF orientation. The integration of experimental observations with polymer simulations is a commendable approach for mechanistically interpreting genomic contact data.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The abstract claims that "experimental observations and polymer simulations indicate that narrow origins of loop extrusion favor jet formation" and that "jets propagate symmetrically for 1-2 Mb, providing an estimate for the range of in vivo loop extrusion."  
  - **Evidence pointer** Abstract text; no specific figures, tables, or methods are referenced  
  - **Concern** The abstract provides no quantitative data, statistical measures, or methodological details to support the claimed relationship between origin width and jet formation, nor the 1-2 Mb propagation range. Without access to the underlying Hi-C data, simulation parameters, and validation metrics, the strength and reliability of these claims cannot be assessed.  
  - **Why it matters** The central novelty of the paper rests on these quantitative claims. If the evidence is weak or the simulations are not well-constrained by experimental data, the conclusions may be overinterpreted. The 1-2 Mb range estimate is a key quantitative output that requires robust support.  
  - **Resolution test** Provide the relevant figures and tables showing jet detection, quantification of propagation distances, and simulation fits to experimental data, along with statistical significance tests and parameter sensitivity analyses.  
  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Mechanistic inference  
  - **Claim pointer** The abstract claims that "asymmetric CTCF binding deflects the angle of jet propagation as experimental evidence that cohesin-mediated loop extrusion can switch from bi- to unidirectional and is controlled independently in both directions."  
  - **Evidence pointer** Abstract text; no specific experimental data or controls are described  
  - **Concern** The inference that asymmetric CTCF binding causes a directional switch in loop extrusion is a strong mechanistic conclusion. The abstract does not describe how CTCF asymmetry was defined, how deflection angles were measured, or whether alternative explanations (e.g., CTCF-independent barriers, chromatin state differences) were excluded.  
  - **Why it matters** This claim directly addresses the regulatory logic of loop extrusion, which is a topic of active debate. If the evidence does not convincingly rule out alternative mechanisms, the conclusion may be premature.  
  - **Resolution test** Show representative contact maps with and without asymmetric CTCF binding, quantify deflection angles across multiple loci, and include controls or perturbations that test the directional control model.  
  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Generalizability  
  - **Claim pointer** The abstract states that jets are "landmarks of loop extrusion in quiescent mammalian lymphocytes" and that the findings "offer new insights into the physiological behavior of in vivo cohesin-mediated loop extrusion."  
  - **Evidence pointer** Abstract text; no data from other cell types or conditions are mentioned  
  - **Concern** The observations are limited to quiescent lymphocytes, and the abstract does not indicate whether jets are observed in other cell types or states. The generalizability of the findings to broader genome organization principles is unclear.  
  - **Why it matters** If jets are specific to quiescent cells or a particular experimental condition, the broader implications for loop extrusion models may be limited.  
  - **Resolution test** Provide evidence from additional cell types or states, or explicitly discuss the scope and limitations of the observations.
- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity of terminology  
  - **Affected element** Definition of "chromatin jets"  
  - **Evidence pointer** Abstract text  
  - **Issue** The term "chromatin jets" is introduced without a precise operational definition. It is unclear whether jets are defined by a specific contact pattern, a quantitative threshold, or a visual feature in Hi-C maps.  
  - **Required correction** Provide a clear definition of jets, including how they are detected and distinguished from other contact patterns such as loops or domains.  
  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Methodological transparency  
  - **Affected element** Polymer simulation details  
  - **Evidence pointer** Abstract text  
  - **Issue** The abstract mentions polymer simulations but does not specify the model type, parameters, or how simulations were matched to experimental data.  
  - **Required correction** Summarize the simulation approach and key parameters in the abstract or refer to specific methods sections.  
  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Quantitative reporting  
  - **Affected element** Propagation range estimate  
  - **Evidence pointer** Abstract text  
  - **Issue** The 1-2 Mb range is stated without confidence intervals or variability measures.  
  - **Required correction** Report the range with appropriate statistical measures or note the basis for the estimate.
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking because the abstract does not provide sufficient evidence to evaluate the central quantitative and mechanistic claims. The lack of visible data, methods, and controls prevents verification of the conclusions.
- **Assessment against Nature-style criteria**  
  - **Originality** The concept of "chromatin jets" appears novel and could offer a fresh perspective on loop extrusion, but the abstract does not demonstrate how this advances beyond existing models of loop extrusion and CTCF boundary function.  
  - **Scientific importance** If substantiated, the findings could refine models of cohesin dynamics and CTCF directionality, which are of broad interest. However, the importance is not fully established from the abstract alone.  
  - **Interdisciplinary readership** The work bridges experimental genomics and polymer physics, which may appeal to a cross-disciplinary audience, but the abstract does not make the interdisciplinary relevance explicit.  
  - **Technical soundness** Cannot be assessed from the abstract; no data, statistics, or methods are visible.  
  - **Readability for nonspecialists** The abstract is reasonably clear but relies on specialized terminology (e.g., "cohesin-propelled," "loop extrusion") without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents an intriguing hypothesis, but the absence of visible data and methods precludes a supportive recommendation. A full manuscript with detailed evidence would be required to assess whether the claims are substantiated.

## Risk / unsupported claims

- The claim that narrow origins of loop extrusion favor jet formation is unsupported in the abstract, as no simulation or experimental data are shown.
- The 1-2 Mb propagation range for in vivo loop extrusion is unsupported without quantitative evidence.
- The claim that asymmetric CTCF binding switches loop extrusion from bidirectional to unidirectional is unsupported without direct experimental demonstration.
- The generalizability of jets as landmarks of loop extrusion beyond quiescent lymphocytes is unassessable from the abstract.