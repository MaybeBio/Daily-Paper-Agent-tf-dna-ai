## GenomeQA: Benchmarking General Large Language Models for Genome Sequence Understanding

Large Language Models (LLMs) are increasingly adopted as conversational assistants in genomics, where they are mainly used to reason over biological knowledge, annotations, and analysis outputs through natural language interfaces. However, existing benchmarks either focus on specialized DNA models trained for sequence prediction or evaluate biological knowledge using text-only questions, leaving the behavior of general-purpose LLMs when directly exposed to raw genome sequences underexplored. We introduce GenomeQA, a benchmark designed to provide a controlled evaluation setting for general-purpose LLMs on sequence-based genome inference tasks. GenomeQA comprises 5,200 samples drawn from multiple biological databases, with sequence lengths ranging from 6 to 1,000 base pairs (bp), spanning six task families: Enhancer and Promoter Identification, Splice Site Identification, Taxonomic Classification, Histone Mark Prediction, Transcription Factor Binding Site Prediction, and TF Motif Prediction. Across six frontier LLMs, we find that models consistently outperform random baselines and can exploit local sequence signals such as GC content and short motifs, while performance degrades on tasks that require more indirect or multi-step inference over sequence patterns. GenomeQA establishes a diagnostic benchmark for studying and improving the use of general-purpose LLMs on raw genomic sequences 1 1 1 Data and code are available at https://anonymous.4open.science/r/GenomeQA-E350 .


## 1 Introduction

Genome analysis has long relied on specialized sequence models and task-specific pipelines. Recent years have seen rapid progress in DNA foundation models that are trained directly on nucleotide sequences, as well as emerging DNA-Text systems that couple a dedicated DNA encoder with a large language model ( 46 ; 11 ; 6 ; 39 ; 12 ; 14 ) . These approaches achieve strong supervised performance, but they typically require task-specific heads, probing, or additional adaptation to support downstream applications. In parallel, large language models have become widely used as conversational assistants across scientific domains, including chemistry ( 19 ; 27 ) , physics ( 3 ; 43 ) , and medicine ( 40 ; 45 ) . In genomics, their most common role is to reason over derived information such as annotations for genes and variants, functional summaries, experimental metadata, literature, and results from existing bioinformatics tools through natural language interfaces. However, direct interaction with raw genomic sequences poses challenges that differ fundamentally from standard natural language processing. DNA lacks human-interpretable semantic units such as words or grammar, exhibits long-range dependencies, and encodes biological signals in highly degenerate and context-dependent patterns ( 9 ; 5 ) . As a result, it remains unclear how general-purpose LLMs behave when they are directly exposed to nucleotide sequences, and whether their responses reflect non-trivial sequence-level cues or are driven primarily by superficial heuristics.

Despite the increasing presence of LLMs in genomics studies, there is currently no standardized benchmark that evaluates how general-purpose language models perform when directly exposed to raw genomic sequences. Existing genome benchmarks ( 28 ; 18 ; 35 ) primarily target trainable DNA-specific models and assess representation quality under fine-tuning or probing. In contrast, exam-style benchmarks ( 7 ; 36 ; 44 ) evaluate biological knowledge using text-only questions without requiring sequence-level analysis. Consequently, a practically important evaluation setting remains underexplored: a general-purpose LLM receiving natural language questions together with raw nucleotide sequences and producing answers under a fixed instruction-following protocol.

We take a step toward filling this gap by introducing GenomeQA, a question-answering benchmark designed to provide a controlled evaluation of general-purpose LLMs on sequence-based genome inference tasks. As shown in Figure 1 , GenomeQA comprises 5,200 samples across six representative task families: Enhancer and Promoter Identification, Splice Site Identification, Taxonomic Classification, Histone Mark Prediction, Transcription Factor Binding Site (TFBS) Prediction, and Transcription Factor (TF) Motif Prediction. Each instance is formatted as either a Binary Choice Question (BCQ) for validity judgment or a four-option Multiple Choice Question (MCQ). To ensure consistent evaluation across models and tasks, we use a single system prompt derived from a small pilot study; the prompt is fixed throughout all experiments and provides domain-relevant guidance for analyzing sequence signals such as motifs and base composition.

Our contributions are summarized as follows:

We introduce GenomeQA, a benchmark that provides a controlled evaluation setting for assessing how general-purpose LLMs perform on sequence-based genome inference tasks. The benchmark comprises 5,200 curated samples spanning six biologically grounded task families.

We conduct a comprehensive evaluation of six frontier LLMs, establishing baseline performance on raw DNA sequences and showing that current models can exploit certain local sequence signals (e.g., GC content and short motifs) but struggle with tasks requiring more complex or indirect inference.

We present a fine-grained analysis of failure modes such as Sequence Motif Over-reliance and Character Fidelity Loss, highlighting systematic error patterns and directions for future research.


## 2 Related Work


## 2.1 Genome-Specific Models

Recent DNA foundation models treat genome sequences as language. They pretrain on billions of nucleotides and add task-specific heads for downstream applications such as regulatory elements prediction and splice site identification. Typical models include DNABERT-2 ( 46 ) , Nucleotide Transformer ( 11 ) , HyenaDNA ( 32 ) , Genos ( 25 ) , GENA-LM ( 15 ) and Evo ( 31 ) . Recent multimodal approaches couple a pretrained DNA foundation model with a general-purpose large language model (LLM), such as ChatNT ( 12 ) , BioReason ( 14 ) and Omni-DNA ( 24 ) . Empirically, these models achieve strong performance and can match or even surpass state-of-the-art results on standard genome understanding benchmarks. Meanwhile, some researchers argue that an alternative route is to repurpose general LLMs into DNA-LLMs directly ( 8 ) , e.g., by adapting tokenization and training objectives so that the LLM can model DNA sequences without an explicit separate DNA encoder. Overall, despite their different interfaces, these methods share a key property: they rely on models that are specifically trained or substantially adapted on DNA sequences.


## 2.2 Genome Benchmarks

Existing benchmarks for genome modeling primarily target models that are specifically designed or adapted for genome data. Sequence-based benchmarks, such as BEND ( 28 ) , DNALongBench ( 9 ) , DART-Eval ( 35 ) , and the Genomics Long-range Benchmark ( 22 ) , are mainly constructed to evaluate genome foundation models. These benchmarks typically consist of raw DNA sequences paired with predefined prediction tasks, and are intended to measure a model’s ability to learn transferable sequence representations for downstream biological applications. Another line of benchmarks focuses on biomedical or clinical knowledge assessment through natural language questions, such as CMExam ( 26 ) , Bio-Benchmark ( 20 ) , and EHRXQA ( 4 ) . While these benchmarks evaluate language understanding and domain knowledge, they do not require models to directly process or reason over raw genomic sequences. More recently, several benchmarks and evaluation protocols have emerged in the context of multimodal genome-language systems, including Lab-Bench ( 23 ) and the task suites used in ChatNT and BioReason. These benchmarks partially involve sequence-based question answering, but they rely on a dedicated genome encoder to transform DNA sequences into latent representations before passing them to a large language model. As a result, the evaluated capability is that of an integrated multimodal system, rather than the intrinsic ability of a general-purpose LLM to interpret DNA sequences. In contrast, GenomeQA is designed to assess general-purpose LLMs in a setting where raw DNA sequences are provided directly as input. Each instance contains real genomic sequences with task-relevant signals, and all tasks are reformulated into a unified natural language question-answering format. GenomeQA does not assume a genome-specific encoder or additional training on DNA data, and is intended to support controlled measurement of LLMs performance on sequence-based genome inference tasks.


## 3 GenomeQA Construction


## 3.1 Design Principles

An overview of the dataset construction pipeline is shown in Figure 1 . GenomeQA is built through a systematic process that transforms curated genome annotations into a unified evaluation framework. (1) We first identify six fundamental task families by collecting high-quality annotations from established databases and repositories, including ENCODE ( 10 ) , EPDnew ( 13 ) , NCBI ( 30 ) , JASPAR ( 38 ) , as well as downstream tasks used in the Nucleotide Transformer (NT) benchmark ( 11 ) . A central design principle is the preservation of biological hierarchy: tasks are grouped to contrast genomic elements at the same functional level (e.g., enhancers versus promoters), rather than mixing signals across disparate biological scales. (2) All selected tasks are processed through a unified three-stage workflow to ensure consistency and data quality. First, we perform interval selection and length standardization to calibrate sequence windows, ensuring that each sequence sufficiently covers the motifs or regulatory signals required for the task. Sequence extraction is conducted using Bedtools ( 37 ) . Second, we remove overlapping samples in six tasks to reduce ambiguity and improve label reliability. Third, a quality control filter is applied to exclude sequences containing ambiguous nucleotide bases. (3) This process concludes with a question formulation stage, where each validated DNA sequence is instantiated into standardized natural language templates. Example question templates are provided in Appendix A.1 . All tasks are presented in either Binary Choice Question (BCQ) or Multiple Choice Question (MCQ) formats. By constraining the answer space and standardizing the question structure, GenomeQA provides a controlled evaluation setting for assessing models’ ability to reason over raw DNA sequences.


## 3.2 Task Families

Enhancer and Promoter Identification. This task focuses on distinguishing cis-regulatory elements in the human genome, specifically promoters and enhancers. Promoter candidates are sourced from EPDnew ( 13 ) , covering regions from 299 base pairs (bp) upstream to 100 bp downstream of the transcription start site. Enhancer candidates are selected from the ENCODE SCREEN database ( 10 ) , with each region centered and resized to match the length of promoter sequences. To ensure that each 400-bp segment corresponds to a single regulatory element, we remove overlapping regions both within and across datasets. The label sets and label statistics are provided in Section A.2 .

Splice Site Identification. This task focuses on human splice acceptor and donor sites. We aggregate positive 600 bp windows from the NT downstream tasks into a unified pool. After that, we relabel windows overlapping by more than 350 bp as containing both elements, while discarding those with shorter overlaps. For questions about the presence of splice sites, we introduce composition-matched negatives by generating dinucleotide-preserving shuffled controls ( 21 ) at construction period, forcing models to rely on higher-order motifs rather than simple base composition cues. The label sets and label statistics are provided in A.3 .

Taxonomic Classification. This task evaluates whether LLMs can recover broad taxonomic groups from sequence alone. We sample 1 kbp fragments from NCBI RefSeq ( 34 ) assemblies representing eukaryote, prokaryote, and virus. Each fragment is assigned a high-level label with approximately balanced sampling across three groups. The complete species list and label statistics are provided in A.4 .

Histone Mark Prediction. This task focuses on the identification of specific histone modifications from genome sequences in human K562 cells. We utilize 10 distinct histone marks from NT downstream tasks, retaining only positive 1 kbp windows. To ensure unique classification, we remove overlapping windows so that each region is associated with exactly one label. Beyond identifying individual marks , we further assess the model’s understanding of functional chromatin states by categorizing some marks as either open(e.g., H3K4me3, H3K27ac, H3K9ac) or repressive(e.g., H3K9me3, H3K27me3). This multi-dimensional annotation enables us to construct questions ranging from specific mark classification to broader chromatin accessibility that test whether the model perceives the underlying functional similarities between different histone modifications. The full histone mark list and label statistics are provided in A.5 .

TFBS Prediction. We design this task to evaluate whether LLMs can accurately identify the specific transcription factor binding sites (TFBS) present in a 100 bp genome window. We select 20 transcription factors (TF) with distinct motifs and source their ChIP-seq peaks from ENCODE. For each TF, we select peak intervals by placing a 100 bp window around the summit and then remove any sample pairs that overlap by more than 70 bp. To obtain precise labels, we scan the remaining sequences with FIMO ( 17 ) using JASPAR position weight matrices (PWM), recording all factors with motif instances in each window. This multi-label dataset enables questions regarding the presence of specific TFs. Additionally, we use CTCF as a canonical architectural protein that organizes chromatin loops and topologically associating domain (TAD) boundaries, constructing questions that test whether models understand its link to 3D genome architecture without naming the factor explicitly. The complete TF list and label statistics are provided in A.6 .

TF Motif Identification. The final task focuses on short motif instances underlying the TFBS prediction task. Using the FIMO results described above, we collect all motif instances for the same 20 transcription factors and deduplicate them, yielding segments from 6 to 20 bp, each associated with a single TF label. Although the questions are linguistically simple, this task probes whether LLMs encode any recognizable representation of canonical transcription factor motifs. The label sets and label statistics are provided in A.7 .


## 3.3 Dataset statistics

Table 1 provides a comprehensive overview of GenomeQA, detailing the biological focus, data sources, sequence lengths, label set sizes, volumes and average length of question instances for each task. Most tasks contribute 500 BCQs and 500 MCQs, while the simpler motif task includes 100 of each. Sequence lengths range from short motifs (6–20 bp) to medium regulatory windows (100–400 bp) and large genome contexts (1 kbp), requiring models to process both local patterns and broader organizational structures. Figure 2 displays the distribution of correct answers across option positions for all tasks. These distributions are nearly uniform, confirming that answer keys are balanced and free from position bias. Together, these metrics indicate that GenomeQA is structurally balanced, ensuring that evaluation results reflect genuine sequence understanding rather than dataset artifacts.


## 4 Experiments and Analysis


## 4.1 Experimental setup

We describe the evaluated models, prompt configuration, and evaluation metrics below.

Baseline Models. We evaluate six state-of-the-art general large language models to assess their capabilities on genome data. The model set includes proprietary frontier models: Claude-Sonnet-4.5 ( 2 ) 2 2 2 Developed by Anthropic. , GPT-5.1 ( 33 ) 3 3 3 Developed by OpenAI. , Gemini-3-Pro ( 16 ) 4 4 4 Developed by Google. We use Gemini-3-Pro-Preview. , Grok-4.1 ( 42 ) 5 5 5 Developed by xAI. We use Grok-4.1-Fast. , Llama-4 ( 29 ) 6 6 6 Developed by Meta. We use Llama-4-Maverick-17B-128E-Instruct. , Qwen3-Max ( 1 ) 7 7 7 Developed by Alibaba. We use Qwen3-Max-Preview. . We enable thinking mode whenever supported for all models to maximize their potential for complex biological deduction.

Prompt Settings. We use a single fixed system prompt across all tasks and models, with details provided in Appendix B . No task-specific few-shot examples are included. The prompt provides domain-relevant guidance and a standardized output format for analyzing sequence signals (e.g., motifs and base composition), ensuring consistency across models while minimizing variation due to prompt design.

Metrics. We select classification accuracy as the evaluation metric. Since the option letters are randomly permuted and correspond to raw DNA sequences rather than stable semantic labels, we calculate accuracy by comparing the model-selected option letter against the ground truth.


## 4.2 Main Results

Table 2 and Figure 3 summarize the performance of the evaluated models on GenomeQA under BCQ and MCQ settings. We highlight three observations. (1) Frontier LLMs outperform random baselines but show substantial performance variation across tasks. Among the evaluated models, Gemini-3-Pro achieves the highest average accuracy (66.27% on BCQ and 60.87% on MCQ), with Claude-Sonnet-4.5, GPT-5.1, and Grok-4.1 forming a closely clustered second tier. In contrast, Llama-4 and Qwen3-Max exhibit lower overall accuracy (e.g., Qwen3-Max achieves 56.87% on BCQ and 41.38% on MCQ). These results indicate that, even for the strongest models, performance on GenomeQA remains weak and inconsistent across tasks. (2) Model performance correlates with task complexity and the depth of reasoning required for each task . As shown in Figure 3 , Large language models achieve respectable accuracy on Enhancer and Promoter Identification, Taxonomic Classification, and TF Motif Prediction as these questions are formatted as direct pattern recognition. In contrast, performance drops significantly on Splice Site Identification, Histone Mark Prediction, and TFBS Prediction. These difficult tasks involve more complex genome signals such as the long-range patterns of histone marks. Furthermore, the framework incorporates indirect reasoning to increase the complexity of these specific tasks. The consistently low accuracy across these categories proves that current LLMs struggle to execute indirect reasoning when they encounter intricate genome data. (3) Multiple choice formats enhance relative discrimination. The random baselines are 50.00% for BCQ and 25.00% for MCQ, with empirical validation provided in Appendix C . Although absolute accuracy is naturally lower in the multiple choice setting, the relative improvement over the baseline is substantially higher. This trend occurs as the format shifts the task from absolute verification to comparative ranking. Unlike isolated binary decisions, the provided options serve as contextual anchors that narrow the search space, enabling models to evaluate relative likelihoods among candidates. Consequently, the performance gain over chance is approximately two-fold higher than in the binary setting. This indicates that the comparative structure effectively leverages the probabilistic ranking capabilities of models to reduce classification noise more robustly than direct verification.


## 4.3 Impact of Thinking Process

To examine the benefits of the explicit reasoning process, we evaluate selected LLMs equipped with the thinking mode. The goal is to assess their ability to perform step-by-step deductions and improve performance on complex genome tasks. We compare the performance of GPT-5.1 and Qwen3-Max by enabling and disabling their thinking features across both binary and multiple-choice settings. As shown in Table 3 , the integration of the thinking process leads to consistent performance gains. Specifically, GPT-5.1 achieves a significant improvement in the multiple-choice setting, where the accuracy increases from 43.97% to 52.30%. This represents a notable enhancement in its ability to filter out distractors. Qwen3-Max also exhibits improvements, although the margins are smaller compared to GPT-5.1. For instance, its binary classification accuracy rises from 54.57% to 56.53%. The disparity in gains between the two models suggests that the effectiveness of the thinking mode depends heavily on the underlying domain knowledge of the base model. These results underscore the importance of enabling thinking capabilities to handle the intricate reasoning required for genome sequence analysis.


## 4.4 Impact of Implicit Target Inference

We design a controlled comparison to evaluate model performance on questions that require an additional inference step beyond direct sequence recognition. We focus on CTCF-related instances in the TFBS Prediction task. CTCF is a canonical transcription factor whose binding sites are strongly associated with higher-order chromatin organization, including chromatin loops and topologically associating domains (TADs). As a result, questions about 3D genome structure can implicitly point to CTCF, which must then be linked back to sequence-level evidence. Specifically, we construct two question variants over the same underlying sequence set. In the direct setting, the question explicitly names the target (CTCF) and asks whether the sequence contains a CTCF binding site, which can be answered by direct pattern recognition. In the indirect setting, the question does not mention CTCF and instead asks whether the sequence is associated with the formation of chromatin loops or TAD boundaries. Answering this variant requires a multi-step mapping: (i) infer the relevant regulatory factor implied by the functional description (CTCF), and (ii) evaluate whether the input sequence contains sequence patterns consistent with that factor. As shown in Table 4 , making the target explicit substantially improves accuracy across models. For example, in the multiple-choice setting, Claude-Sonnet-4.5 and GPT-5.1 increase from 27.11% to 63.86%, and Gemini-3-Pro increases from 44.58% to 67.47%. In contrast, performance in the inference setting is often close to the random baseline. These results suggest that the additional target-inference step is a major source of difficulty in this setting.


## 4.5 Failure Case Study

To gain a deeper understanding of the limitations of current LLMs in genome analysis, we analyze 200 error samples produced by Gemini-3-Pro. As shown in Figure 4 , our qualitative analysis categorizes these failures into four distinct types, revealing the cognitive disconnect between general LLM and the rigorous requirements of genomics. Details are provided in Appendix D .

Sequence Motif Over-reliance (SMO, 47%). Failures occur when models rely on general sequence elements while neglecting specific details. For instance, in Histone Mark Prediction, the model incorrectly classifies an open Alu repeat as closed ( 41 ) . It simply applies the general rule that transposable elements are repressed and overlooks the high GC content of this specific element.

Base Composition Over-reliance (BCO, 32%). Failures occur when models rely on statistical summaries while ignoring structural patterns. For instance, in Taxonomic Classification, the model incorrectly identifies a virus as a prokaryote. It uses the high GC content as a shortcut and ignores the specific gene organization that actually points to a virus.

Character Fidelity Loss (CFL, 13%). Models frequently lose character-level fidelity in long sequences, leading to the fabrication of non-existent sub-sequences to support their claims. In Enhancer and Promoter Identification, the model hallucinates a specific motif sequence as evidence that does not actually exist within the input sequence.

Noise Distinction Failure (NDF, 8%). Failures occur when models fail to recognize meaningless patterns in shuffled negative samples. For instance, in Splice Site Identification, the model analyzes a randomized control sequence. It fails to detect the random nature of the input and performs a pseudo-analysis to incorrectly classify it as a splice site.


## 5 Conclusion

We introduce GenomeQA, a benchmark designed to support systematic evaluation of general-purpose large language models on sequence-based genome inference tasks. By curating biologically grounded tasks across multiple genomic contexts and adopting standardized question formats, GenomeQA provides a controlled evaluation setting for analyzing model performance on raw DNA sequences. Our experimental results show that current LLMs can leverage certain local sequence signals but exhibit substantial performance variation across tasks, particularly when targets are implicit or require additional inference steps. These findings highlight both the current limitations of general-purpose LLMs in this setting and the need for more reliable evaluation tools. We hope GenomeQA will serve as a useful diagnostic resource for future research on genome-aware language modeling and the integration of LLMs with genomic data.


## Limitations

We acknowledge two primary limitations of this work. (1) Benchmark scale. Evaluating multiple frontier LLMs under thinking-enabled settings incurs substantial computational cost. For example, Claude-Sonnet requires on the order of minutes to process a single sample, and Qwen3-Max can take even longer. To balance inference cost with task coverage, we curate a high-quality but moderately sized dataset. As a result, while GenomeQA is suitable for systematic evaluation, its current scale is not intended for full-parameter fine-tuning of large models. (2) Task scope. GenomeQA focuses on foundational sequence-based tasks such as motif recognition and coarse taxonomic classification. More complex biological problems, including variant effect prediction, and gene expression modeling, are not covered. These tasks typically require much longer sequences that exceed current context window limits and depend on additional modalities such as chromatin accessibility, histone modifications, and three-dimensional genome structure. Extending GenomeQA to incorporate such multi-omics signals is an important direction for future work.


## Ethical considerations

Our GenomeQA benchmark is built upon publicly available genome databases and established biological datasets, which are open for academic and research purposes. Additionally, we have rigorously reviewed the benchmark to ensure strict adherence to ethical guidelines. The dataset consists of de-identified public reference sequences and contains no personally identifiable information or private human genetic data. We have also verified that the benchmark focuses solely on fundamental biological understanding and contains no content related to biosecurity risks, harmful pathogens, or inappropriate material.


## References


## Appendix A Details for GenomeQA construction


## A.1 Question Templates

As described in Section 3.1 , we formulate two distinct question types: Binary Choice Questions (BCQ) and Multiple Choice Questions (MCQ). For each type, we curate a set of templates that were generally applied consistently across most tasks. While the template structure remains largely consistent across most tasks, we introduce specialized templates for the Splice Site Prediction, Histone Mark Prediction, and Transcription Factor Binding Site (TFBS) Prediction tasks to slightly increase the complexity of the tasks. Comprehensive examples of these templates are presented in Table 5 .


## A.2 Enhancer and Promoter Identification

For the Enhancer and Promoter Identification task, the label set is comprised of enhancer and promoter.

In this task, each sequence corresponds to a single, mutually exclusive label. We analyze the distribution of question types to verify dataset balance, as described in Figure 5 (a) and Figure 5 (b). In the Binary Choice Questions, the distribution is nearly symmetrical with 257 questions targeting enhancers and 243 targeting promoters. Similarly, the Multiple Choice Questions maintain this balanced approach featuring 244 enhancer-related queries and 256 promoter-related queries. This uniform distribution ensures that the model is evaluated equally on its ability to identify both regulatory elements.


## A.3 Splice Site Identification

For the Splice Site Identification task, the label set is comprised of acceptor, donor and both patterns.

In this task, each sequence corresponds to a single splice site category. In the Binary Choice Questions, the distribution remains relatively comparable across the three classes, with 176 questions targeting acceptors, 188 targeting donors, and 136 focusing on dual-site sequences. This balance extends to the Multiple Choice Questions, which feature an almost perfect split: 172 acceptor, 163 donor, and 165 both-related queries. Such a distribution guarantees that the performance metrics reflect a holistic understanding of all splice site configurations rather than a bias toward a specific type. The details are provided in Figure 5 (c) and Figure 5 (d).


## A.4 Taxonomic Classification

In this task, the label set encompasses Eukaryote, Prokaryote, and Virus categories. We source eukaryotic sequences from Homo sapiens, Mus musculus, and Sus scrofa. For Prokaryotes, we select three common bacterial species. To address the shorter length of viral DNA, we utilize 9 viral species to ensure a sufficient number of candidate samples. Table 6 provides detailed specifications.

In this task, each sequence corresponds to a single taxonomic category, classifying inputs as Eukaryote, Prokaryote, or Virus. We analyze the distribution of question types to verify dataset balance, as described in Figure 5 (e) and Figure 5 (f). In the Binary Choice Questions, the dataset exhibits a well-proportioned composition across the three domains, with 170 questions targeting eukaryotes, 150 targeting prokaryotes, and 180 focusing on viral sequences. This balanced structure is mirrored in the Multiple Choice Questions, which feature a comparable distribution: 177 eukaryote, 165 prokaryote, and 158 virus-related queries. Such uniform coverage ensures that the model is rigorously evaluated on its ability to distinguish genome signatures across diverse biological domains without bias.


## A.5 Histone Mark Prediction

We utilize all 10 histone marks from the downstream Nucleotide Transformer dataset for the recognition task. Building on this, we select five histone marks to construct the chromatin accessibility task, consisting of three marks from open regions and two from closed regions. The "Undefined" represents the normal usage. Table 7 contains detailed information.

In this task, each sequence corresponds to a single histone modification mark. The detailed information are provided in Figure 5 (g) and Figure 5 (h). Unlike the strictly uniform distributions in other tasks, the data here reveals an intentional skew in both Binary and Multiple Choice Questions. This deviation arises from the introduction of a Chromatin Accessibility reasoning dimension. To construct questions specifically focusing on open versus closed chromatin states, we prioritized a subset of five markers: three associated with open regions (H3K4me3, H3K27ac, H3K9ac) and two with closed regions (H3K9me3, H3K27me3). Consequently, questions targeting these five labels appear significantly more frequently than those targeting the remaining markers in the set, reflecting a design choice to stress-test the model’s understanding of chromatin structure.


## A.6 TFBS Prediction

As described in Section 3.2 , we select 20 transcription factors with distinct motif patterns from the JASPAR database, as Figure 6 illustrates. On this basis, we choose six factors to construct the 3D genome structure correlation task. Among these, CTCF associates with 3D architecture through its role in forming TADs and loops. The label Undefined indicates standard usage without contributing to additional problem dimensions. Table 8 provides detailed specifications.

In this task, while genome sequences naturally contain multiple binding motifs (multi-label), each question interrogates the presence of a specific target Transcription Factor selected from a set of 20. The details are provided in Figure 5 (i) and Figure 5 (j). Similar to the Histone Mark task, the data exhibits a deliberate distributional skew across both Binary and Multiple Choice Questions. To evaluate the model’s understanding of chromatin architecture, we significantly oversampled six specific TFs: CTCF, a key architectural protein facilitating TADs and loops, and SP1, GABPA, E2F1, TEAD4, and NRF1. Consequently, questions targeting these six factors dominate the statistics compared to the remaining 14 labels, prioritizing the assessment of structural regulatory logic over a uniform distribution.


## A.7 TF Motif Identification

We use the same label set as in the TFBS task. In this task, we do not differentiate between whether a factor is associated with 3D genome structure.

In this task, each sequence corresponds to a single dominant motif selected from a set of 20 transcription factors. The statistics are shown in Figure 5 (k) and Figure 5 (l). In the Binary Choice Questions, the sampling is uniformly distributed across the 20 categories, ensuring no single motif dominates the evaluation. Similarly, the Multiple Choice Questions maintain this balanced approach, featuring an equitable distribution of target queries across the entire label set. This uniform coverage guarantees that the model’s ability to recognize short consensus patterns is tested fairly across diverse biological contexts without class bias.


## Appendix B System Prompt Optimization

To ensure that the evaluation accurately reflects the genome reasoning capabilities of Large Language Models (LLMs) rather than their sensitivity to prompt engineering, we conduct an ablation study to derive an optimized system prompt. This prompt aims to maximize the models’ ability to interpret DNA sequences by providing clear domain constraints and reasoning protocols.


## B.1 Development Set Construction

To balance computational cost with statistical representativeness, we construct a small-scale development set comprising 90 samples. We employ a stratified sampling strategy by randomly selecting three samples for each unique combination of problem type, task category, and specific problem dimension. This selection spans binary and multiple-choice formats across tasks such as TFBS prediction and splice site identification, including specific dimensions like 3D genome structure correlation. This compact yet diverse dataset serves as the testbed for iterative prompt refinement.


## B.2 Optimization Strategy

The optimization process follows a two-stage iteration starting with a baseline prompt generated by Gemini 3 Pro, as Figure 7 illustrates. This initial text provides a general persona of a computational biology expert and standard instructions to analyze sequences. We conduct manual error analysis on the model outputs and observe that models frequently hallucinate constraints or refuse to answer due to a perceived lack of evidence. To address this, we manually refine the text into the Optimized System Prompt presented in Figure 8 . Key enhancements include explicitly instructing models to choose the most likely option based on probabilistic signals, defining six specific biological domains to narrow the search space, and mandating a structured analysis of motif organization. This final requirement specifically aids in distinguishing real sequences from dinucleotide-preserved shuffled controls.


## B.3 Performance Validation

We evaluate the effectiveness of the optimized prompt against the baseline across six LLMs on the development set. As the ablation studies in Table 9 and Table 10 demonstrate, the optimized prompt consistently matches or outperforms the baseline version. Across all six evaluated models, the optimized prompt yields performance gains in at least three out of six tasks per model. The improvement is particularly notable in tasks requiring subtle pattern recognition, where the explicit instruction to avoid hedging forces models to leverage weak biological signals for decision-making.


## Appendix C Empirical Baseline Verification

To validate the reliability of using theoretical probability as a performance floor, we calculate empirical random baselines by simulating random guessing across all evaluation tasks. We compare these empirical values against the standard theoretical expectations of 50.00% for Binary Choice Questions (BCQ) and 25.00% for Multiple Choice Questions (MCQ).

As presented in Table 11 , the empirical results align closely with theoretical expectations. The average empirical accuracy across all tasks is 51.17% for BCQ and 25.23% for MCQ, exhibiting only negligible deviations from the theoretical values. The overall consistency confirms that the theoretical baselines serve as accurate and fair proxies for zero-knowledge performance in our main analysis.


## Appendix D Case Study

Figure 9 presents examples of four failure modes in genome analysis: Sequence Motif Over-reliance (SMO), Base Composition Over-reliance (BCO), Character Fidelity Loss (CFL), and Noise Distinction Failure (NDF). Each example includes the input context, model output, and an analysis of the error. These cases highlight distinct cognitive gaps in general LLMs: prioritizing general sequence elements over specific details (SMO), using statistical shortcuts like GC content while ignoring structural patterns (BCO), losing character-level fidelity to fabricate non-existent sub-sequences (CFL), and the sycophantic tendency to rationalize random noise as valid biological signals (NDF). These examples illustrate the systematic error patterns in current LLMs and underscore the need for domain-aligned reasoning capabilities.