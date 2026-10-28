## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce ChatNT, a multimodal conversational agent for DNA, RNA and protein tasks. They claim state-of-the-art results on the Nucleotide Transformer benchmark, simultaneous multi-task solving in English, generalization to unseen questions, performance on par with specialized methods on newly curated biologically relevant instruction tasks, and a novel perplexity-based confidence calibration technique. The framework is described as easily extensible to other modalities.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, dataset descriptions, or methodological specifics are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, benchmark definitions, dataset curation details, model architecture description, training procedures, baseline comparisons, statistical analyses, and code availability

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially valuable contribution that bridges biological foundation models and conversational agents. The concept is timely and the claimed capabilities are impressive. However, the abstract alone provides insufficient evidence to evaluate the validity of the central claims. Key quantitative results, benchmark protocols, and methodological details are absent. The claim of "first multimodal conversational agent" requires careful contextualization against existing work. The perplexity-based calibration technique is mentioned but not described in any detail. The abstract reads more as a programmatic vision than a verifiable scientific report.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on genomic language models would be interested in the extension of foundation models to conversational interfaces. Machine learning researchers focused on multimodal agents and instruction tuning would find the framework relevant. Biologists without programming expertise who need accessible tools for sequence analysis would benefit from the described capabilities. The work also has potential relevance for clinicians and researchers in personalized medicine who require natural language interfaces to genomic data.
- **Major strengths** The conceptual contribution of bridging conversational agents with biological sequence understanding is novel and potentially impactful. The emphasis on accessibility for non-coders addresses a real limitation of existing foundation models. The proposed extensibility to other modalities suggests a scalable framework. The inclusion of DNA, RNA, and protein tasks within a single model is ambitious and could reduce fragmentation in the field.
- **Major Concerns** The abstract provides no quantitative evidence for any of the stated claims. The Nucleotide Transformer benchmark results are asserted without numbers, baselines, or statistical context. The claim of "performance on par with state-of-the-art specialized methods" is unverifiable without specific task definitions and comparison metrics. The "novel perplexity-based technique" is mentioned but not explained. The generalization to unseen questions is asserted without any demonstration. The curation of new instruction tasks is described but no details on data sources, quality control, or task diversity are given.
- **Minor Comments** The term "first multimodal conversational agent" requires careful qualification given the rapid pace of the field. The phrase "advanced understanding of biological sequences" is vague and needs operational definition. The relationship between the Nucleotide Transformer benchmark and the newly curated tasks is unclear. The abstract does not specify the model architecture or parameter count. The claim of solving "all tasks at once" needs clarification regarding computational and memory requirements.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: The concept of a conversational agent for biological sequences is genuinely novel and could represent a significant advance. Scientific importance: If the claims are substantiated, the work could lower barriers to genomic analysis and enable broader access to foundation model capabilities. Interdisciplinary readership: The work bridges machine learning, genomics, and user interface design, which could attract readers from multiple communities. Technical soundness: Cannot be assessed from the abstract alone; no methodological details or results are provided. Readability for nonspecialists: The abstract is generally clear and accessible, though some terms such as "perplexity-based technique" and "instruction-tuning" may require explanation for a broader audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a compelling vision but lacks the quantitative and methodological substance required to evaluate the scientific claims. A full manuscript with detailed results, benchmark protocols, and comparisons would be necessary to assess whether the case is established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "ChatNT achieves new state-of-the-art results on the Nucleotide Transformer benchmark"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract asserts state-of-the-art performance on the Nucleotide Transformer benchmark without providing any numerical results, comparison baselines, or evaluation protocol details. No information is given about which tasks within the benchmark were used, how many runs were performed, or what statistical significance was achieved.
- **Why it matters** State-of-the-art claims are central to the paper's contribution and require rigorous quantitative support. Without specific numbers and comparison details, the claim cannot be verified or contextualized against existing methods.
- **Resolution test** Provide a table with performance metrics on all Nucleotide Transformer benchmark tasks, including baseline results, standard deviations, and statistical tests demonstrating superiority.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "ChatNT reaches performance on par with state-of-the-art specialized methods on those tasks"
- **Evidence pointer** Abstract; location not provided
- **Concern** The newly curated instruction tasks are described but not specified. No task list, dataset sizes, evaluation metrics, or comparison methods are provided. The claim of parity with specialized methods cannot be assessed without knowing which methods were compared and on which tasks.
- **Why it matters** This claim is essential to demonstrate that the conversational approach does not sacrifice performance for accessibility. Without task definitions and comparison details, the claim is unfalsifiable.
- **Resolution test** Provide a detailed description of the curated tasks, including data sources, preprocessing, evaluation metrics, and a comparison table against specialized baselines with statistical analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "generalize to unseen questions"
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract claims generalization to unseen questions but provides no definition of what constitutes an "unseen question," no experimental protocol for testing generalization, and no results demonstrating this capability.
- **Why it matters** Generalization is a key differentiator from fine-tuned models and is central to the claim of a generally capable agent. Without a clear evaluation protocol, this claim is ambiguous and unverifiable.
- **Resolution test** Define the generalization protocol, including how unseen questions were generated, how they differ from training data, and provide quantitative results showing successful generalization with appropriate baselines.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological clarity
- **Claim pointer** "a novel perplexity-based technique to help calibrate the confidence of our model predictions"
- **Evidence pointer** Abstract; location not provided
- **Concern** The perplexity-based calibration technique is mentioned but not described. No details are given on how perplexity is computed, how it is mapped to confidence scores, or how calibration quality was evaluated.
- **Why it matters** Confidence calibration is important for practical deployment, especially in biomedical contexts where incorrect predictions could have serious consequences. The novelty claim requires a clear description of the method and evidence of its effectiveness.
- **Resolution test** Provide a detailed description of the calibration method, including mathematical formulation, and demonstrate its effectiveness using calibration metrics such as expected calibration error or reliability diagrams.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "the first multimodal conversational agent with an advanced understanding of biological sequences"
- **Evidence pointer** Abstract; location not provided
- **Concern** The claim of being "the first" requires a thorough literature review demonstrating that no prior work has combined conversational interfaces with biological sequence understanding. The abstract provides no comparison with or discussion of existing conversational agents in biology.
- **Why it matters** Priority claims are significant in scientific publishing and must be supported by comprehensive literature analysis. An unsupported "first" claim could mislead readers and misrepresent the state of the field.
- **Resolution test** Provide a literature review section that systematically surveys existing conversational agents in biology and clearly demonstrates the novelty of ChatNT relative to prior work.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "multimodal" is used to describe the agent, but the abstract only mentions DNA, RNA, and protein sequences as input modalities. It is unclear whether this refers to multiple sequence types or to genuinely different data modalities such as structure or imaging.
- **Required correction** Clarify the definition of "multimodal" in the context of this work and specify which modalities are currently supported.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Resource availability
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not mention whether the model, code, or curated datasets will be made publicly available. This is important for reproducibility and for the claimed extensibility of the framework.
- **Required correction** State clearly in the abstract or main text whether code, models, and datasets will be released and under what license.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope definition
- **Affected element** Task coverage
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract mentions tasks spanning "multiple species, tissues and biological processes" but does not provide any examples or indication of the breadth of coverage.
- **Required correction** Provide a brief summary of the task categories and the diversity of species, tissues, and processes covered in the curated instruction tasks.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparative positioning
- **Affected element** Baseline selection
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract does not specify which "specialized methods" were used as baselines for the curated tasks. Without this information, the parity claim is difficult to interpret.
- **Required correction** Name the specific baseline methods and justify their selection as representative of the state of the art.

## Risk / unsupported claims
- The claim of state-of-the-art results on the Nucleotide Transformer benchmark is unsupported by any quantitative data in the abstract.
- The claim of performance parity with specialized methods on curated tasks is unsupported without task definitions and comparison results.
- The claim of generalization to unseen questions is unsupported without a defined evaluation protocol.
- The claim of being "the first multimodal conversational agent" is unsupported without a literature review.
- The "novel perplexity-based technique" is described but not explained, making its novelty and effectiveness unassessable.
- The claim that the framework is "easily extensible" to other modalities is an assertion without supporting evidence or architectural details.