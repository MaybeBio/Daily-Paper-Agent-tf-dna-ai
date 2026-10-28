## Review setup
- **Input scope** Full manuscript text as provided
- **Assessment boundary** Methodological description, virtual screening workflow, and reported outcomes only
- **Shared manuscript claim summary** The authors describe a multi-pronged virtual screening campaign targeting two sub-pockets of the SARS-CoV2 NSP13 RNA-binding site, using the FITTED docking program with rigid and flexible docking, followed by consensus scoring from four approaches (docking score, graph neural network, quantum mechanics, visualization), supplemented by templated docking with co-crystallized fragments. The manuscript states that experimental testing is pending and will be reported in a future update.
- **Visible evidence base** Abstract and main text as provided, including workflow description and statement of pending experimental validation
- **Missing materials affecting confidence** No figures, tables, structural data, docking scores, compound lists, or experimental results are provided. The manuscript is explicitly incomplete, with experimental outcomes awaited.

## Reviewer
- **Overall assessment** This manuscript describes a computational workflow for a community challenge, but in its current form it is a methods-in-progress report rather than a complete scientific study. The approach is reasonable and the use of consensus scoring is sensible, but the absence of any results, validation data, or comparative analysis means the claims cannot be assessed. The manuscript is transparent about its incomplete status, which is commendable, but this does not yet constitute a publishable scientific contribution.
- **Who would be interested in the results, and why** Computational chemists and drug discovery researchers interested in virtual screening methodologies, particularly those working on SARS-CoV2 targets or using consensus scoring approaches. The templated docking implementation within FITTED may be of interest to developers and users of docking software. However, the lack of results limits the audience until experimental data are available.
- **Major strengths** The use of multiple orthogonal scoring methods (docking score, machine learning, quantum mechanics, visualization) is a thoughtful approach to reduce false positives in virtual screening. The implementation of templated docking to leverage co-crystallized fragments is a practical and potentially valuable addition. The commitment to open science and updating the manuscript with experimental results is commendable.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The manuscript provides no quantitative results, no validation of the consensus scoring approach, no comparison to alternative methods, and no experimental confirmation. The core claims about the effectiveness of the workflow cannot be evaluated without these data.
- **Assessment against Nature-style criteria**  
  - Originality: The combination of consensus scoring with templated docking is not entirely novel, but the specific application to NSP13 and the integration of four scoring methods has some originality. However, without results, the novelty cannot be demonstrated.  
  - Scientific importance: The target is relevant to COVID-19 treatment, but the importance of this specific computational contribution is unclear without validation.  
  - Interdisciplinary readership: The work sits at the interface of computational chemistry, structural biology, and drug discovery, which could attract a broad audience, but the current lack of results limits appeal.  
  - Technical soundness: The described methods are plausible, but no evidence is provided to assess their correctness or performance.  
  - Readability for nonspecialists: The text is clear and accessible, but the absence of figures or data makes it difficult for any reader to follow the workflow in detail.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript is a preliminary methods description with no results. It could become publishable if experimental data are added and the workflow is validated, but in its present form it does not meet the standards for a scientific contribution.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The manuscript claims that the multi-pronged virtual screening approach and consensus scoring will effectively identify compounds targeting the NSP13 RNA-binding pocket.  
- **Evidence pointer** Main text, "we evaluated predicted poses from the VS using four approaches" and "final selection being based on the consensus of all four approaches"  
- **Concern** No results are presented. There are no docking scores, no compound lists, no enrichment analyses, no comparison to known binders, and no experimental validation. The entire claim of effectiveness rests on the description of the workflow, not on any demonstrated outcome.  
- **Why it matters** Without results, the reader cannot judge whether the consensus approach improves hit rates, whether the templated docking adds value, or whether the selected compounds are likely to be active. The scientific case is entirely unsubstantiated.  
- **Resolution test** Provide the full results of the virtual screening, including the number of compounds screened, the number selected, the scores from each of the four methods, and any experimental binding or activity data once available.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological validation  
- **Claim pointer** The manuscript implies that the consensus scoring method and templated docking are reliable for this target.  
- **Evidence pointer** Main text, "we implemented templated docking within FITTED to take advantage of fragments co-crystallized with NSP13"  
- **Concern** There is no validation of the templated docking implementation. No test cases, no comparison to standard docking, no assessment of whether the templated approach improves pose prediction or enrichment. The method is described but not demonstrated.  
- **Why it matters** A new or modified docking method requires validation to establish that it performs as intended. Without such validation, the reliability of the results, even when they become available, is questionable.  
- **Resolution test** Provide a validation study for the templated docking, such as redocking of co-crystallized ligands, enrichment tests on known actives, or comparison to the standard FITTED protocol.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Completeness  
- **Claim pointer** The manuscript states that the authors "await the experimental testing of our predictions" and will update the manuscript accordingly.  
- **Evidence pointer** Main text, "We now await the experimental testing of our predictions by the Structural Genomics Consortium"  
- **Concern** The manuscript is explicitly incomplete. It is a progress report, not a finished study. The core outcome, whether the predictions are correct, is unknown.  
- **Why it matters** A scientific manuscript must present a complete study with results and conclusions. This manuscript presents only a plan and a workflow, with no findings. It cannot be evaluated as a scientific contribution.  
- **Resolution test** Add the experimental results when available, including binding affinities or activities of the selected compounds, and discuss the success or failure of the predictions.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract, "we targeted each of two sub-pockets of the NSP13 RNA-binding site"  
- **Issue** The abstract does not specify which two sub-pockets are targeted or how they are defined. This is important for reproducibility.  
- **Required correction** Name the sub-pockets and provide a reference or structural definition.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods description  
- **Evidence pointer** Main text, "using the latest functionality in FITTED"  
- **Issue** The version of FITTED and the specific parameters used for docking are not described. This prevents others from reproducing the workflow.  
- **Required correction** Provide the software version, parameter settings, and any custom modifications.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Presentation  
- **Affected element** Figures and tables  
- **Evidence pointer** Location not provided  
- **Issue** No figures or tables are included, making it difficult to visualize the workflow or the binding sites.  
- **Required correction** Add a figure showing the NSP13 structure with the two sub-pockets highlighted, and a flowchart of the consensus scoring pipeline.

## Risk / unsupported claims
- The claim that the consensus scoring approach will effectively identify active compounds is unsupported, as no results are presented.
- The claim that templated docking supplements the consensus selection is unsupported, as no validation or example is given.
- The claim that the workflow targets the RNA-binding pocket of NSP13 is plausible but not demonstrated with structural figures or docking poses.
- The overall effectiveness of the virtual screening campaign cannot be assessed, as experimental outcomes are pending and not included.