## Ctrl-DNA: Controllable Cell-Type-Specific Regulatory DNA Design via Constrained RL

Designing regulatory DNA sequences that achieve precise cell-type-specific gene expression is crucial for advancements in synthetic biology, gene therapy and precision medicine. Although transformer-based language models (LMs) can effectively capture patterns in regulatory DNA, their generative approaches often struggle to produce novel sequences with reliable cell-specific activity. Here, we introduce Ctrl-DNA , a novel constrained reinforcement learning (RL) framework tailored for designing regulatory DNA sequences with controllable cell-type specificity. By formulating regulatory sequence design as a biologically informed constrained optimization problem, we apply RL to autoregressive genomic LMs, enabling the models to iteratively refine sequences that maximize regulatory activity in targeted cell types while constraining off-target effects. Our evaluation on human promoters and enhancers demonstrates that Ctrl-DNA consistently outperforms existing generative and RL-based approaches, generating high-fitness regulatory sequences and achieving state-of-the-art cell-type specificity. Moreover, Ctrl-DNA -generated sequences capture key cell-type-specific transcription factor binding sites (TFBS), short DNA motifs recognized by regulatory proteins that control gene expression, demonstrating the biological plausibility of the generated sequences.

Code available at: github.com/bowang-lab/Ctrl-DNA


## 1 Introduction

Cis-Regulatory elements (CRE), such as promoters and enhancers, are critical DNA sequences that control gene expression. The ability to engineer DNA sequences with precise regulatory activities has widespread implications in biotechnology, including gene therapy, synthetic biology, and precision medicine gosai2024machine ; boye2013comprehensive . A particularly desirable but challenging goal is designing CREs that drive high gene expression in a target cell type while maintaining controlled or limited fitness 1 1 1 CRE fitness is defined as the ability to enhance gene expressions. in off-target cell types. A CRE’s regulatory function is largely determined by its transcription factor binding sites (TFBSs), which are short DNA motifs recognized by transcription factors (TFs) that mediate gene regulation in cells. The presence or absence of specific TFBSs directly influences the fitness of a sequence across different cellular contexts. Although millions of regulatory sequences have evolved naturally gao2020enhanceratlas , these sequences are not optimized for targeted biomedical applications. For example, despite the human body comprising over 400 distinct cell types, very few cell-type-specific promoters have been identified reddy2024designing . This scarcity highlights the need for novel, engineered CREs with precise cell-type specificity. However, the design space for regulatory sequences is immense: a 100-base sequence yields approximately 4 100 4^{100} possibilities, making purely experimental approaches expensive and impractical.

Massively parallel reporter assays (MPRAs) have significantly advanced our ability to evaluate large libraries of DNA sequences for their cell-type-specific fitness tewhey2016direct ; de2020deciphering . Building upon these assays, recent deep learning approaches leverage predictive models as reward functions to guide the optimization of CREs gosai2024machine ; taskiran2024cell . However, these methods typically rely on iterative optimization strategies based on mutating existing or randomly initialized sequences, which often limits the sequence diversity and can trap optimization in local optima. Furthermore, enforcing complex constraints in multiple cell types is non-trivial in these frameworks.

Recent studies have adapted autoregressive language models (LMs) for regulatory DNA sequence design, successfully capturing functional sequence patterns and enabling the generation of sequences with desired properties, such as enhanced gene expression levels reglm . However, these models primarily imitate the distribution of known sequences, limiting their ability to explore novel regions of the sequence landscape. Reinforcement learning (RL) has emerged as an approach to finetune genomics LMs for optimizing DNA sequence design. However, existing RL-based approaches for cell-type-specific CRE design typically focus on maximizing fitness in a target cell type without accounting for fitness in other cell types taco . To date, integrating explicit constraints within RL frameworks to suppress off-target regulatory activity using genomic LMs remains unexplored. Furthermore, conventional RL optimization strategies often depend on accurate value models and dense reward signals, introducing increased difficulty and inefficiency when navigating the vast DNA sequence space with complex biological constraints and sparse fitness reward signals.

To address these limitations, we introduce Ctrl-DNA , a reinforcement learning framework for controllable cell-type-specific regulatory DNA design via constrained RL. To the best of our knowledge, this work represents one of the first efforts to design regulatory DNA sequences with precise and controllable cell-type specificity. Building on recent advances in RL deepseekr1 ; constraintppo ; lagppo , we develop an RL-based fine-tuning framework based on pre-trained autoregressive genomic LMs. Our method avoids value model training by incorporating Lagrangian-regularized policy gradients directly from batch-normalized rewards, enabling stable and efficient optimization across multiple cell types. Ctrl-DNA supports explicit cell-type-specific constraints, enabling the generation of sequences with high expression in target cell types while constraining off-target activities. We evaluate Ctrl-DNA on human promoter and enhancer design tasks across six cell types. Our results show that Ctrl-DNA consistently outperforms existing generative and RL-based methods, achieving higher activity in target cell types while improving constraint satisfaction in non-target cell types. We also show that Ctrl-DNA -generated sequences maintain substantial sequence diversity and effectively capture biologically meaningful, cell-type-specific regulatory motifs.

Our main contributions are as follows:

We develop a novel constraint-aware RL framework for CRE design, utilizing Lagrange multipliers explicitly and effectively to control cell-type specificity. To our knowledge, this represents one of the first efforts to incorporate constraint-based optimization into regulatory sequence generation.

By directly computing policy gradients from batch-normalized biological rewards and constraints, our method eliminates the need for computationally expensive value models, enabling efficient learning under complex CRE design constraints.

Through extensive empirical evaluations on human promoter and enhancer design tasks, we demonstrate that Ctrl-DNA consistently outperforms existing generative and RL-based methods, achieving higher targeted regulatory activity with state-of-the-art cell-type specificity.


## 2 Related Works

DNA Sequence Design Optimization : Optimization strategies complement generative models by explicitly steering sequences toward desired functions. Classical evolutionary algorithms, such as genetic algorithms, iteratively refine sequences using fitness predictors, but they are often computationally expensive and may converge to suboptimal solutions vaishnav2022evolution . To improve efficiency, heuristic techniques such as greedy search have been developed, incrementally editing sequences toward higher predicted performance gosai2024machine . Gradient-based approaches leverage differentiable surrogate models (e.g., neural predictors like Enformer) to perform gradient ascent directly in sequence space reddy2024designing ; linder2021fast . Although computationally efficient, these methods often initialize from random or high-fitness observed sequences, reducing the diversity of generated sequences. Reinforcement learning (RL) offers a powerful framework that combines generative modelling with goal-directed optimization. DyNA-PPO Dyna-ppo demonstrated the effectiveness of deep RL for DNA design, outperforming random mutation-based methods. GFlowNets further advanced this direction by learning stochastic policies that align with reward distributions, enabling diverse exploration of sequence space GFlowNet . More recently, TACO taco used RL to fine-tune pretrained DNA language models with biologically informed rewards. However, these approaches primarily focus on optimizing fitness in a single target cell type, without mechanisms to suppress or constrain activity in undesired cell types.

Constrained Reinforcement Learning : Constrained Reinforcement Learning (CRL), or often formulated as constrained Markov decision processes (CMDPs), addresses the critical challenge of optimizing policies under explicit constraints. Early foundational studies include actor-critic methods borkar2005actor and constrained policy optimization with function approximation bhatnagar2012online . Subsequent studies have explored integrating constraints into RL, often using Lagrangian methods that introduce non-stationarity into rewards tessler2018reward ; stooke2020responsive ; ding2023provably . Regularized policy optimization augments standard objectives with Kullback–Leibler (KL) or trust-region constraints schulman2015trust , and is widely used in both single-task abdolmaleki2018maximum and multi-task settings moskovitz2022towards . CRL has been applied in language generation to suppress undesired outputs through techniques like Lagrangian reward shaping constraintppo ; lagppo ; moskovitz2023confronting , balancing primary objectives with safety constraints. However, such approaches remain largely unexplored in regulatory DNA design, where sparse rewards and multiple cell-type-specific constraints introduce significant challenges for standard constrained RL frameworks.


## 3 Methods


## 3.1 Problem Formulation

We formulate DNA sequence design as a constrained Markov decision process (CMDP). A DNA sequence is defined as X = ( x 1 , x 2 , … , x L ) ∈ V L X=(x_{1},x_{2},\ldots,x_{L})\in V^{L} , where V = { A , C , G , T } V=\{\text{A},\text{C},\text{G},\text{T}\} is the nucleotide vocabulary and L L is the sequence length. The CMDP is defined as ℳ = ( 𝒮 , 𝒜 , p , R 0 , { R i } i = 1 m , { δ i } i = 1 m ) \mathcal{M}=(\mathcal{S},\mathcal{A},p,R_{0},\{R_{i}\}_{i=1}^{m},\{\delta_{i}\}_{i=1}^{m}) , where 𝒮 \mathcal{S} is the state space, 𝒜 = V \mathcal{A}=V is the action space. p ⁡ ( s t + 1 ∣ s t , a t ) p(s_{t+1}\mid s_{t},a_{t}) is a transition function that appends nucleotide a t a_{t} to the current sequence prefix s t s_{t} . The sequence is evaluated by m m black-box reward functions { R i : V L → ℝ } i = 0 m \{R_{i}:V^{L}\rightarrow\mathbb{R}\}_{i=0}^{m} , where we denote reward R 0 R_{0} as the CRE fitness in target cell, and reward R i R_{i} for i ≥ 1 i\geq 1 as CRE fitness in off-target cell types. The values δ i ∈ ℝ \delta_{i}\in\mathbb{R} is the constraint threshold for off-target cell i i . At each time step t t , the agent observes state s t = ( x 1 , … , x t − 1 ) ∈ 𝒮 s_{t}=(x_{1},\ldots,x_{t-1})\in\mathcal{S} , selects an action a t ∈ 𝒜 a_{t}\in\mathcal{A} according to a policy π θ ​ ( a t ∣ s t ) \pi_{\theta}(a_{t}\mid s_{t}) , and transitions to the next state s t + 1 s_{t+1} . Rewards { R i ​ ( X ) } \{R_{i}(X)\} are only calculated at the terminal step t = L t=L .

Our objective is to learn a policy π θ \pi_{\theta} that maximizes the expected CRE fitness in the target cell type while ensuring off-target fitness remains within the specified constraints. Formally, we aim to solve:

For clarity, we define J i ​ ( θ ) = 𝔼 X ∼ π θ ​ [ R i ​ ( X ) ] J_{i}(\theta)=\mathbb{E}_{X\sim\pi_{\theta}}[R_{i}(X)] as the expected reward for cell type i i , where J 0 ​ ( θ ) J_{0}(\theta) is referred to as task rewards and J i ​ ( θ ) J_{i}(\theta) for i ≥ 1 i\geq 1 is referred to as constraints(also called off-target rewards throughout this paper).


## 3.2 Constrained Batch-wise Relative Policy Optimization

We now describe our approach for solving the constrained reinforcement learning problem for CRE sequence generation introduced in Section 3.1 . Most deep-learning-based constrained RL methods rely on training one or more value models to estimate expected returns and costs constraintppo ; focops ; lagppo , which can significantly increase training complexity. Moreover, reward signals that are sparse and only available at the end of a generated sequence may further complicate the training of value models that need accurate values at each step shao2024deepseekmath .

To address this, we adapt work in shao2024deepseekmath ; deepseekr1 for our constrained DNA sequence design task, avoiding value network training for each cell type while enforcing constraints on off-target cell CRE fitness. We adopt a primal-dual approach based on Lagrangian relaxation, which introduces adaptive multipliers to enforce constraints while optimizing the main objective.

Lagrangian Relaxation and Constrained RL. The Lagrangian relaxation of the constrained objective in Eq. 1 defines a primal-dual optimization problem:

where δ i \delta_{i} is a user-specified threshold and λ i ≥ 0 \lambda_{i}\geq 0 is a dual variable for constraint i i .

In practice, we solve primal-dual policy optimization by taking iterative gradient ascent-descent steps of the policy parameter θ \theta and Lagrangian multiplier λ i \lambda_{i} :

where η θ \eta_{\theta} and η λ i \eta_{\lambda_{i}} are learning rates. k k denotes the optimization step. This min-max formulation seeks a saddle point that maximizes reward while satisfying constraints ding2023provably ; constraintppo .

Our Methods. As commonly done in reinforcement learning REINFORCE ; schulman2017proximal , ∇ θ J ​ ( θ ) \nabla_{\theta}J(\theta) is calculated by policy gradient methods where ∇ θ J ​ ( θ ) = 𝔼 π ​ [ Ψ t ​ ∇ θ ​ log ⁡ π θ ​ ( a t ∣ s t ) ] \nabla_{\theta}J(\theta)=\mathbb{E}_{\pi}\left[\Psi_{t}\nabla_{\theta}\log\pi_{\theta}(a_{t}\mid s_{t})\right] . Ψ t \Psi_{t} represents a surrogate signal such as rewards, state-action values or advantage estimates GAE . While standard approaches compute advantages using learned value functions, we avoid value network training by drawing inspirations from the Group Relative Policy Optimization (GRPO) framework deepseekr1 ; shao2024deepseekmath . GRPO estimates advantages by comparing outputs generated from the same prompt. In contrast, we propose a batch-level variant for CRE sequence optimization, where advantages are computed by grouping sequences within each training batch.

Formally, for each objective i ∈ { 0 , … , m } i\in\{0,\ldots,m\} , the normalized advantage for sequence X j X_{j} is defined as A i ( j ) = R i ​ ( X j ) − R ¯ i σ ⁡ ( R i ) A_{i}^{(j)}=\frac{R_{i}(X_{j})-\bar{R}_{i}}{\sigma(R_{i})} , where R i ​ ( X j ) R_{i}(X_{j}) is the reward assigned by the i i -th reward function, and R ¯ i \bar{R}_{i} , σ ⁡ ( R i ) \sigma(R_{i}) denote the batch mean and standard deviation of R i R_{i} over the current batch of sequences. To guide policy updates under constraints, we use the Lagrange multipliers to form a convex combination of advantages from different cell types. We define the Lagrangian advantage as:

where m m is the number of constraints, and λ i ( j ) \lambda_{i}^{(j)} is the Lagrange multiplier applied for constraint i i . This encourages the policy to favor sequences with high target rewards while discouraging those that violate constraints.

To estimate ∇ θ J ​ ( θ ) \nabla_{\theta}J(\theta) during policy updates, we adopt a clipped surrogate objective with KL regularization deepseekr1 ; schulman2017proximal :

where π θ \pi_{\theta} and π old \pi_{\text{old}} denote the current and previous policy networks. π ref \pi_{\text{ref}} is the reference model, which usually is the initial policy model. Here, ρ i ( j ) = π θ ​ ( a i j ∣ s i j ) π old ​ ( a i j ∣ s i j ) \rho_{i}^{(j)}=\frac{\pi_{\theta}(a_{i}^{j}\mid s_{i}^{j})}{\pi_{\text{old}}(a_{i}^{j}\mid s_{i}^{j})} is the importance sampling ratio, and clip ϵ ​ ( ρ i ( j ) ) = clip ​ ( ρ i ( j ) , 1 − ϵ , 1 + ϵ ) \text{clip}_{\epsilon}(\rho_{i}^{(j)})=\text{clip}(\rho_{i}^{(j)},1-\epsilon,1+\epsilon) restricts large policy updates. The coefficient β \beta controls the strength of the KL divergence penalty, and ϵ \epsilon sets the clipping threshold.

To adaptively enforce constraints, we update the Lagrangian multiplier λ i \lambda_{i} based on batch-level constraint satisfaction. For each constraint i i , we define the multiplier loss as ℒ multiplier ​ ( λ i ) = 1 B ​ ∑ j = 1 B ( R i ( j ) − δ i ) ​ λ i \mathcal{L}_{\text{multiplier}}(\lambda_{i})=\frac{1}{B}\sum_{j=1}^{B}\left(R_{i}^{(j)}-\delta_{i}\right)\lambda_{i} , where δ i \delta_{i} is the constraint for cell type i i . This formulation increases the penalty on off-target cell types whose predicted fitness exceeds the constraint thresholds, while reducing the weight of those that already satisfy the constraints.

With this setup, the primal-dual updates (Equation 3 & 4 ) become:

Detailed pseudocode for the full algorithm and gradient functions are provided in Appendix A .

Empirical Designs. To improve training stability and model performance, we introduce several empirical modifications. First, we maintain a replay buffer of previously generated sequences and mix them with samples from the current policy. This helps reduce variance in batch-level reward statistics and leads to smoother advantage estimation. Second, we clip each Lagrange multiplier λ i \lambda_{i} to the range [ 0 , 1 ] [0,1] , which prevents overly aggressive constraint enforcement and stabilizes the dual updates. Lastly, to prevent the main objective from being overwhelmed when constraint weights are large, we clip its coefficient in Eq. 5 as min ⁡ ( 1 , m − ∑ i = 1 m λ i ) \min(1,m-\sum_{i=1}^{m}\lambda_{i}) , ensuring sufficient signal for optimizing the target reward.


## 3.3 Regularizing Generated Sequences via TFBS Frequency Correlation

Although Ctrl-DNA effectively optimizes sequence generation under specified constraints, the resulting sequences may still deviate from biologically realistic distributions due to reward hacking gao2023scaling . To further regularize the generated distribution toward biologically plausible patterns, we introduce an additional reward term based on the correlation between transcription factor binding site (TFBS) frequencies in generated and real sequences.

Specifically, we first compute TFBS frequencies from a reference set of real DNA sequences. For each TFBS, we calculate its occurrence frequency across these real sequences, forming a reference frequency vector q real q_{\text{real}} . Similarly, for each sequence generated by the policy π θ \pi_{\theta} , we compute a corresponding motif frequency vector q gen q_{\text{gen}} . We then quantify the similarity between generated and real sequence distributions using the Pearson correlation coefficient: R TFBS ​ ( X ) = Corr ​ ( q gen , q real ) R_{\text{TFBS}}(X)=\text{Corr}(q_{\text{gen}},q_{\text{real}}) for each generated sequence X X .

We treat R TFBS R_{\text{TFBS}} as an additional constraint reward function to maintain realistic TFBS patterns in generated sequences. However, to prevent the policy from overfitting to correlation alone and generating sequences that merely replicate the real distribution, we apply a clipped upper bound on the corresponding dual multiplier λ TFBS \lambda_{\text{TFBS}} . That is, from Equation 4 , we clip λ T ​ F ​ B ​ S \lambda_{TFBS} to the range [ 0 , λ m ​ a ​ x ] [0,\lambda_{max}] where λ m ​ a ​ x ≤ 1 \lambda_{max}\leq 1 . where λ max \lambda_{\text{max}} is a predefined hyperparameter. This clipping mechanism ensures a balanced optimization process that maintains realistic TFBS frequencies without overly constraining policy exploration or the main optimization objective.

TFBS information is widely used in CRE design reglm ; reddy2024designing ; sarkar2024designing . However, existing methods typically incorporate TF motifs either as post-hoc evaluation metrics or through explicit tiling strategies during sequence design. A closely related approach is TACO taco , which trains a LightGBM model to predict sequence fitness from motif frequencies and derives motif-level rewards from SHAP values. In contrast, our method bypasses the need for additional predictive models by directly aligning the motif frequency distribution of generated sequences with that of real sequences. This removes the potential biases introduced by model training and provides a more reliable regularization signal from real biological distributions.


## 4 Experiments


## 4.1 Experimental Setup

Datasets. We evaluate our method on human promoter and enhancer datasets gosai2023machine ; promoter_dataset . The enhancer dataset includes 200 bp sequences from three cell lines: HepG2, K562, and SK-N-SH. The promoter dataset consists of 250 bp sequences from Jurkat, K562, and THP1. Each dataset contains sequence-fitness pairs across the three respective cell types, with fitness measured via massively parallel reporter assays (MPRAs) mrpa . We adopt the preprocessing pipeline described in reglm to preprocess all datasets. Please refer to Appendix B for details.

Motif Processing and Real Sequence Statistics. We obtain human-specific position probability matrices (PPMs) and pairwise motif correlation data from the JASPAR 2024 database castro2022jaspar . Following the preprocessing procedure described in reglm , we retain a curated set of 464 human transcription factor motifs. For each task, we identify real sequences by selecting those in the top 50th percentile for fitness in the target cell type and the bottom 50th percentile in off-target cell types. We then apply FIMO fimo to scan for motif occurrences and compute motif frequency distributions, which serve as the reference motif distribution for optimization and evaluation.

Models and Baselines. We adopt the Enformer architecture enformer to train cell-type-specific reward models, following protocols from previous CRE design studies reglm ; taco ; reddy2024designing ; sarkar2024designing ; gosai2023machine . For sequence generation, we fine-tune HyenaDNA nguyen2023hyenadna , an autoregressive genomic LM pre-trained on the human genome, as our policy model. We compare our proposed method, Ctrl-DNA , against a diverse set of baselines, including evolutionary algorithms (AdaLead sinai2020adalead , BO bo , CMAES cmaes , PEX pex ), generative models (regLM reglm ), and reinforcement learning approaches (TACO taco , PPO schulman2017proximal , PPO-Lagrangian lagppo ). Full baseline details are provided in Appendix C .

Evaluation Metrics. To assess the performance of each method, we report median rewards ( Median ) over the generated sequences in the final round. Additionaly, we report Reward Difference ( Δ ​ R \Delta R ) to quantify the average difference between the target cell’s fitness and the fitness across off-target cell types, indicating the cell-type fitness specificity. Motif Correlation is defined as the Pearson correlation between TFBS frequencies in generated sequences and real sequences. A higher correlation indicates greater alignment with biologically plausible motif distributions. Lastly, Diversity is calculated as the Shannon entropy of the generated sequences in the final round, reflecting the model’s ability to explore diverse solutions. We report the mean and standard deviation of each metric over 5 runs initialized with different random seeds.


## 4.2 Ctrl-DNA optimizes enhancer and promoter sequences under cell-type-specific constraints

We evaluate Ctrl-DNA on two regulatory sequence design tasks using the Human Enhancer and Human Promoter datasets. Results are presented in Figure 2 . In these plots, points positioned further to the right indicate lower fitness in off-target cell types (i.e., better constraint satisfaction), while points higher on the vertical axis indicate higher fitness in the target cell type. Methods that appear in the upper-right corner achieve the best trade-off between maximizing target cell fitness and minimizing off-target expression.

For enhancers, we evaluate performance under three constraint thresholds ( δ = 0.3 , 0.5 , 0.6 \delta=0.3,0.5,0.6 ). Across all thresholds, Ctrl-DNA consistently achieves the highest target-cell fitness while satisfying the off-target constraints. PPO-Lagrangian (PPO-Lag) struggles to balance optimization and constraint satisfaction, likely due to the difficulty of training value networks under sparse, sequence-level reward signals. Notably, while methods such as TACO and CMAES achieve relatively high expression in the target cell type, they fail to suppress off-target fitness, leading to poor cell-type specificity.

The promoter design task is a more challenging task because all three target cell types are mesoderm-derived hematopoietic cells, which share substantial transcriptional similarity reddy2024designing . We test under three constraint thresholds ( δ = 0.4 , 0.5 , 0.6 \delta=0.4,0.5,0.6 ). Ctrl-DNA outperforms all baselines in maximizing target cell-type fitness and satisfying constraints at δ = 0.5 \delta=0.5 and 0.6 0.6 . However, no method, including Ctrl-DNA , successfully reduces THP1 fitness below the stricter threshold of δ = 0.4 \delta=0.4 . We hypothesize that this is due to the data distribution: the 25th percentile of THP1 fitness is already 0.49 (Appendix B ), indicating that most sequences exhibit high expression in this cell type. Despite this challenge, when THP1 is treated as an off-target cell, Ctrl-DNA still achieves the lowest THP1 fitness among all methods.

Across both enhancer and promoter tasks, Ctrl-DNA consistently achieves the best trade-off between optimizing target cell types and enforcing cell-type-specific constraints, substantially outperforming existing RL and generative baselines. Interestingly, we observe a clear trade-off when enforcing stricter constraints: as the constraint threshold decreases, the fitness in the target cell type slightly declines. This trend likely arises because stricter constraint enforcement potentially narrows the feasible sequence space, making it more challenging to simultaneously optimize target cell-type activity and minimize off-target expression. Despite this inherent difficulty, Ctrl-DNA ’s constraint-aware optimization framework remains highly effective, demonstrating robustness in maintaining superior target-cell fitness even under rigorous constraint conditions.


## 4.3 Ctrl-DNA captures biologically relevant motifs with higher specificity

Besides the fitness of generated CRE sequences in each cell type, we also evaluate the sequences with three other metrics: reward difference ( Δ ​ R \Delta R ), motif correlation and diversity. In Table 1 , we can observe that Ctrl-DNA achieves highest reward differences across all cell types in both human promoter and enhancers, indicating it is better at optimizing DNA sequences for cell-specific fitness. For motif correlation, Ctrl-DNA also achieves stronger performance across most cell types, except for THP1 in promoter design. As noted in Section 4.2 , THP1 fitness values are skewed, with the majority of sequences in the dataset exhibiting fitness around 0.5. Since motif correlation is evaluated against sequences near the 50th percentile (see Section 4.1 ), the resulting motif frequency distribution may not accurately reflect the high-activity sequences we aim to design.

To further investigate this discrepancy, we extract motifs from promoter sequences in the 90th percentile of THP1 fitness, applying a significance threshold of q < 0.05 q<0.05 to avoid false positives. We then re-evaluate the motif correlation between generated sequences and this more selective reference set. These results, denoted as Motif Corr † \dagger in Table 1 , show that Ctrl-DNA outperforms all baselines under this stricter setting. In contrast, most baseline methods exhibit reduced motif correlation, suggesting that they tend to align with non-informative or broadly distributed motifs. Despite being regularized using motifs from a less selective reference set, Ctrl-DNA successfully prioritizes the most discriminative motifs during optimization.

To further demonstrate that Ctrl-DNA selects more cell-type-discriminative motifs during sequence generation, we evaluated the frequency of known cell-type-specific TFBS in the generated sequences. In particular, we examined generated sequences for liver-specific and erythropoietic-specific motifs. As shown in Figure 3 a, Ctrl-DNA -generated sequences for HepG2 (a liver-derived cell line) show the highest frequency of liver-specific motifs such as HNF4A and HNF4G. Similarly, sequences generated for K562 (an erythropoietic lineage cell line) contain the highest frequency of erythropoietic-specific motifs such as GATA1 and GATA2. These findings indicate that Ctrl-DNA not only optimizes for target-cell fitness, but also learns regulatory patterns that reflect underlying cell-type specificity.

Finally, we assess the diversity of generated sequences in Figure 3 b and Appendix D . Ctrl-DNA achieves comparable or higher diversity than most baselines, indicating its ability to generate diverse sequences without sacrificing regulatory control.


## 4.4 Ablation Study

Constraint Formulations. To investigate alternative constraint enforcement strategies, we explored several other constrained methods from current works. First, we adapt the loss from Interior-point Policy Optimization (IPO) liu2020ipo , referring to this variant as Ctrl-DNA-IPO . Second, we implement a log-barrier penalty on constraint rewards following rewardguided , which we denote as Ctrl-DNA-Log . All experiments are conducted using a constraint threshold of 0.5 0.5 . See Appendix E for detailed setup. As shown in Table 2 , Ctrl-DNA-Log suppresses off-target rewards effectively but fails to maintain high fitness in the target cell type. In contrast, Ctrl-DNA-IPO improves target reward but does not enforce constraints adequately. These results highlight that our proposed formulation strikes a better balance between optimizing target cell-type fitness and minimizing off-target expression.

TFBS Regularization. In Section 3.3 , we introduced a correlation-based regularization using TFBS motif frequencies to promote biologically plausible sequences. By changing the upper bound on the TFBS multiplier ( λ max \lambda_{\max} ) we can limit the weight we put on this regularization. From Table 2 , we observe that increasing λ max \lambda_{\max} from 0.0 to 0.1 improves motif correlation without substantially degrading other metrics. In certain cell types, such as JURKAT, a higher value of λ max \lambda_{\max} also leads to improved optimization performance (See Appendix Table 7 ). This supports the utility of TFBS regularization in guiding sequence generation. However, since our comparisons use motif frequencies computed from a loosely matched reference set, we recommend tuning λ max \lambda_{\max} carefully in practical applications depending on the reliability of the available ground truth.


## 5 Discussion

Designing cell-type-specific cis-regulatory sequences presents a challenging optimization problem that involves balancing competing objectives. Our proposed method, Ctrl-DNA , achieves strong performance across both enhancer and promoter datasets, outperforming evolutionary and RL baselines in maximizing target cell-type fitness while satisfying off-target constraints. In addition, Ctrl-DNA supports explicit control over constraint thresholds, enabling flexible and controllable CRE sequence design. By computing Lagrangian advantages directly from batch-normalized rewards without training value models, Ctrl-DNA offers a lightweight and effective solution to constrained CRE DNA sequence generation.

Nevertheless, the ability to enforce constraints is inherently limited by the data distribution. For instance, in the THP1 promoter dataset, a large proportion of sequences exhibit high baseline activity, making it difficult to enforce stricter constraints such as δ = 0.4 \delta=0.4 . This challenge affects both the accuracy of the learned reward model and the capacity of Ctrl-DNA to suppress expression in such settings. These observations highlight the importance of considering dataset-specific characteristics when setting constraint thresholds or evaluating constrained RL methods.

Although Ctrl-DNA already demonstrates robust performance, there are several directions for improvement. First, tuning Lagrange multipliers remains empirical. Future work could explore adaptive control methods such as proportional–integral–derivative controllers pid . Second, additional biological constraints could be incorporated to further improve the plausibility and functionality of generated sequences. Finally, our current framework is limited to reinforcement learning fine-tuning on autoregressive models. As a next step, we plan to extend Ctrl-DNA to other structures such as diffusion-based DNA models.


## References


## Appendix A Training Details for Ctrl-DNA

We provide a high-level overview of our constrained reinforcement learning procedure for optimizing constraint-aware regulatory sequence generation. We also present the hyperparameter settings used in our experiments in Table 3 . All models were trained using the Adam optimizer with a learning rate specified in Table 3 with 100 training epochs.

Experiments were conducted on a single NVIDIA A100 GPU with 40 GB of memory. Each experiment typically required between 1 to 2 hours of wall-clock time. The experiment results reported are mean performances across five seeds.


## A.1 Policy Optimization Objective

As discussed in Section 3.2 , the objective for updating policy parameters θ \theta is defined as:

where ρ i ( j ) = π θ ​ ( a i j ∣ s i j ) π old ​ ( a i j ∣ s i j ) \rho^{(j)}_{i}=\frac{\pi_{\theta}(a_{i}^{j}\mid s_{i}^{j})}{\pi_{\text{old}}(a_{i}^{j}\mid s_{i}^{j})} is the importance sampling ratio, and clip ϵ ​ ( ρ i ( j ) ) = clip ​ ( ρ i ( j ) , 1 − ϵ , 1 + ϵ ) \text{clip}_{\epsilon}(\rho^{(j)}_{i})=\text{clip}(\rho^{(j)}_{i},1-\epsilon,1+\epsilon) applies clipping for stability. Following shao2024deepseekmath , we assume one policy update per iteration, allowing π old = π θ \pi_{\text{old}}=\pi_{\theta} for simplification.

The gradient of this objective with respect to θ \theta becomes:


## A.2 Lagrangian Multiplier Update

We apply Lagrangian relaxation to enforce soft constraints on off-target cell types. The gradient of the multiplier objective with respect to each Lagrange multiplier λ i \lambda_{i} is given by:

where R i ​ ( X j ) R_{i}(X_{j}) is the constraint-specific reward (e.g., off-target activity) for sample X j X_{j} , and δ i \delta_{i} is the user-defined constraint threshold.


## Appendix B Dataset

In this section, we describe the datasets used in our experiments. The human enhancer dataset contains cis-regulatory element (CRE) activity measured by MPRA across three cell lines: HepG2 (liver cell line), K562 (erythrocyte cell line), and SK-N-SH (neuroblastoma cell line). Each sequence in this dataset is 200 base pairs long.

The human promoter dataset contains promoter activity (CRE fitness) measured from three leukemia-derived cell lines: JURKAT, K562, and THP1. All three are mesoderm-derived hematopoietic cell lines and share high biological similarity. Each sequence in this dataset is 250 base pairs in length. Compared to enhancer datasets that span multiple germ layers and tissue types, optimization and constraint satisfaction in the promoter dataset is more challenging due to the biological similarity between the cell lines reddy2024designing .

We provide percentile statistics of normalized activity scores in Tables 4 and 5 . Notably, in the THP1 cell line, even the 25th percentile activity reaches 0.49, suggesting a right-skewed distribution. This distributional bias may partially explain the increased difficulty in constraining THP1 activity, as discussed in Section 4.2 .


## Appendix C Baselines

In this section, we provide detailed descriptions of all baseline methods compared in the main paper:

AdaLead sinai2020adalead : A hill-climbing evolutionary algorithm that uses a novelty-guided search strategy to explore high-fitness sequences.

Bayesian Optimization (BO) sinai2020adalead : A black-box optimization method that models the fitness function with a Gaussian process surrogate and selects new candidates by maximizing an acquisition function.

CMA-ES cmaes : A population-based evolutionary algorithm that adapts a multivariate Gaussian distribution over iterations. We apply CMA-ES on one-hot encoded sequence representations.

PEX pex : An evolutionary approach that prioritizes generating high-fitness variants with minimal mutations relative to the wild-type sequence.

RegLM reglm : An autoregressive model trained to generate cis-regulatory element (CRE) sequences conditioned on cell-type-specific fitness signals.

TACO taco : A reinforcement learning method based on REINFORCE REINFORCE , which incorporates transcription factor motif rewards to guide generation toward high-fitness sequences.

PPO schulman2017proximal : A widely used policy optimization algorithm that updates policies using clipped surrogate objectives to ensure stable training.

PPO-Lagrangian lagppo : A constrained variant of PPO that incorporates Lagrangian relaxation to balance main rewards and constraint satisfaction.


## Appendix D Sequence Diversity

In this section, we report the full results of sequence diversity for Ctrl-DNA and baseline methods as shown in Figure 4 .


## Appendix E Extended Ablation Results

This section provides additional results and implementation details for the ablation experiments introduced in Section 4.4 . We evaluate ablations on both the Human Enhancer and Human Promoter datasets.

Ctrl-DNA-Log. Following the reward-guided approach proposed in rewardguided , we implement a log-barrier transformation of the constraint reward. Specifically, we define a log-augmented reward as

where R 0 R_{0} is the target reward, R i R_{i} is the constraint reward for i ≥ 1 i\geq 1 , c c is the threshold, and c 1 c_{1} is a small constant for numerical stability. We then compute normalized advantages using this transformed reward:

We replace the mixed advantages in the original loss function (Equation 6 ) with A log ( j ) A^{(j)}_{\text{log}} . All other settings (e.g., surrogate loss, clipping, KL regularization) remain the same as in Ctrl-DNA .

Ctrl-DNA-IPO. Based on Interior Policy Optimization (IPO) liu2020ipo , we incorporate the log-barrier directly into the optimization objective. The surrogate loss becomes:

where the log-barrier penalty is defined as

with t > 0 t>0 controlling the sharpness of the approximation to the indicator function. A larger t t yields a tighter barrier. We set t = 50 t=50 in our experiments. Note that, unlike the main Ctrl-DNA method, this variant does not compute mixed advantages as in Equation 5 . Instead, we compute advantages using only the target reward:


## Appendix F Additional Related Work

Generative Models for Biological Sequence Design : Deep generative models have advanced the design of functional DNA sequences. Diffusion-based approaches have emerged as promising tools, beginning with the Dirichlet Diffusion Score Model (DDSM), which creates promoters based on expression levels avdeyev2023dirichlet . Building on this foundation, several subsequent studies have further developed diffusion models for designing regulatory DNA sequences senan2024dna ; li2023latent ; sarkar2024designing . Researchers have also leveraged Generative Adversarial Networks (GANs) for regulatory sequence design, with taskiran2024cell creating cell-type-specific enhancers in Drosophila and humans, and ExpressionGAN zrimec2022controlling generates yeast promoters that outperform natural sequences in expression efficiency. Autoregressive genomic language models have recently been applied to model DNA sequences, learning statistical patterns from large-scale genomic datasets. For example, RegLM reglm fine-tuned the HyenaDNA model nguyen2023hyenadna using prefix tokens that encode expression levels, allowing the generation of enhancers with controlled activity. However, despite producing biologically plausible sequences, generative models typically replicate distributions observed in training data, constraining their ability to explore novel, out-of-distribution solutions. This inherent limitation underscores the need for integrating generative approaches with optimization frameworks such as reinforcement learning.