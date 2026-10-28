## Training-Free Bayesianization for Low-Rank Adapters of Large Language Models

Estimating the uncertainty of responses of Large Language Models (LLMs) remains a critical challenge. While recent Bayesian methods have demonstrated effectiveness in quantifying uncertainty through low-rank weight updates, they typically require complex fine-tuning or post-training procedures. In this paper, we propose T raining- F ree B ayesianization ( TFB ), a novel framework that transforms existing off-the-shelf trained LoRA adapters into Bayesian ones without additional training. TFB systematically searches for the maximally acceptable level of variance in the weight posterior, constrained within a family of low-rank isotropic Gaussian distributions. We theoretically demonstrate that under mild conditions, this search process is equivalent to variational inference for the weights. Through comprehensive experiments, we show that TFB achieves superior uncertainty estimation and generalization compared to existing methods while eliminating the need for complex training procedures. Code will be available at https://github.com/Wang-ML-Lab/bayesian-peft .


## 1 Introduction

Despite recent advances in Large Language Models (LLMs) showing great capacity for generating responsive answers to human instructions ( Biderman et al. 2023 ; Wei et al. 2022 ; Wei et al. 2021 ; Min et al. 2022 ; Chowdhery et al. 2023 ; Anil et al. 2023 ; Touvron et al. 2023a ; Touvron et al. 2023b ; Radford et al. 2019 ; Brown et al. 2020 ; Achiam et al. 2023 ; OpenAI 2022 ) , the reliability of such large models remains a critical concern for researchers ( Wang et al. 2024b ; Wang et al. 2024a ) , as untruthful yet confident answers could cause significant damage to individuals and society ( Gupta et al. 2024 ; Nikitin et al. 2024 ; Yadkori et al. 2024 ; Kapoor et al. 2024 ) . The accurate estimation of uncertainty in LLMs has thus emerged as a crucial challenge. Current research approaches mainly follow two paths: one focuses on eliciting models’ internal (verbalized) uncertainty through direct questioning ( Xiong et al. 2023 ; Tian et al. 2023 ; Kapoor et al. 2024 ) , while the other employs fine-tuning ( Kapoor et al. 2024 ; Wang et al. 2024d ) or post-training procedures ( Yang et al. 2023 ) .

Both approaches face inherent limitations. Verbalized uncertainty, while simple to implement, remains controversial in terms of its empirical reliability and theoretical soundness ( Kadavath et al. 2022 ; Kuhn et al. 2023 ) . On the other hand, low-rank adapters (LoRA ( Hu et al. 2022 ) ), which offer a parameter-efficient way to adapt LLMs by adding a small set of low-rank weight matrices, have emerged as a promising direction for fine-tuning models. However, while LoRA efficiently adapts large models to new tasks, it does not itself provide a mechanism for principled uncertainty estimation. Recent Bayesianization attempts, such as BLoB ( Wang et al. 2024d ) , integrate Bayesian methods with LoRA but still require complex training procedures and delicate hyperparameter tuning, limiting their practicality . These constraints motivate the following research question:

Can we “Bayesianize” a low-rank adapter in a theoretically sound and empirically simple way?

In this paper, leveraging the existing abundance of trained LLM adapters across various domains, we diverge from conventional fine-tuning and post-training approaches. Instead, we develop a Training-Free Bayesianization ( TFB ) technique applicable to any given low-rank LLM adapter. TFB constrains the family of full-weight posteriors produced by LoRA adapters to low-rank isotropic Gaussian distributions. Given a trained LoRA adapter, it systematically searches for the maximally acceptable variance of the variational distribution of the weight posterior. TFB ’s search range and stopping criteria can be determined using any additional in-distribution “anchor dataset,” independent of its supervision status or prior use in LoRA training.

Despite its straightforward approach, we theoretically demonstrate that under mild conditions, TFB ’s process of finding the maximal variance of the isotropic Gaussian posterior is equivalent to variational inference given an isotropic Gaussian prior with sufficiently large variance.

Through extensive empirical evaluation across various settings, datasets, LLM backbones, LoRA weights, and LoRA variants, we verify TFB ’s effectiveness. Our comprehensive experiments demonstrate that this novel training-free Bayesianization framework consistently achieves superior generalization and more accurate uncertainty quantification. To summarize, the main contributions of this paper are:

We propose Training-Free Bayesianization ( TFB ), the first framework to transform trained LoRA adapters into Bayesian ones without re-training, continued training, or even gradient estimation.

We establish theoretical connections between TFB and Variational Inference (VI), proving the equivalence between our variance maximization and variational free energy minimization under mild conditions.

We develop an efficient, practical implementation requiring only an anchor dataset for search, making it widely applicable across different domains and compatible with various LoRA variants.

Through comprehensive experiments, we demonstrate TFB consistently improves uncertainty estimation for off-the-shelf LoRA adapters, and overall surpasses the state-of-the-art counterparts of Bayesian LoRA.

Notation. Scalars, vectors, and matrices are denoted by lowercase letters, lowercase boldface letters, and uppercase boldface letters, respectively. For a matrix 𝑿 = [ 𝒙 1 , ⋯ , 𝒙 n ] ∈ ℝ m × n {\bm{X}}=[{\bm{x}}_{1},\cdots,{\bm{x}}_{n}]\in\mathbb{R}^{m\times n} , we use vec ⁡ ( 𝑿 ) = [ 𝒙 1 ⊤ , 𝒙 2 ⊤ , ⋯ , 𝒙 n ⊤ ] ⊤ ∈ ℝ ( m ​ n ) × 1 \operatorname{vec}({\bm{X}})=[{\bm{x}}_{1}^{\top},{\bm{x}}_{2}^{\top},\cdots,{\bm{x}}_{n}^{\top}]^{\top}\in\mathbb{R}^{(mn)\times 1} to denote vectorization. ⊗ \otimes and ∘ \circ are used to denote the Kronecker and element-wise product, respectively.


## 2 Related Work

LLM Uncertainty Estimation. To estimate the uncertainty of large language models (LLMs), the models themselves are often employed to generate and evaluate their own uncertainty ( Lin et al. 2022 ; Kadavath et al. 2022 ) . However, such approaches typically rely on task-specific labels and require additional training. Semantic entropy ( Kuhn et al. 2023 ) leverages the invariance of language stemming from shared meanings to estimate uncertainty, while mutual information is used to compute a lower bound on model uncertainty by sampling from the model’s output distribution ( Yadkori et al. 2024 ) . Despite their contributions, these methods fail to accurately capture true model uncertainty, as they do not model the probability distribution over the parameter space ( Hüllermeier & Waegeman 2021 ; Abdar et al. 2021 ; Gawlikowski et al. 2023 ) .

Bayesian Low-Rank Adaptation. The Bayesian framework provides a powerful approach for capturing and estimating uncertainty by defining prior distributions and approximating posterior distributions over the parameter space ( Neal 2012 ; Hernández-Lobato & Adams 2015 ; Gal & Ghahramani 2016 ; Wang & Yeung 2016 ; Gustafsson et al. 2020 ) . However, modeling parameter distributions across the entire parameter space during fine-tuning introduces significant computational overhead ( Fan et al. 2020 ; Zhang et al. 2021 ) . To address this challenge, recent research has explored combining Bayesian methods with Parameter-Efficient Fine-Tuning (PEFT) techniques to improve the efficiency of uncertainty estimation. Several notable approaches have emerged in this direction. Wang et al. 2023 and Balabanov & Linander 2024 demonstrate improved performance by training multiple LoRA modules and ensemble their predictions during inference. Taking a different approach, Yang et al. 2023 applies a Kronecker-factorized Laplace approximation to fine-tuned LoRA parameters. More recently, BLoB ( Wang et al. 2024d ) advances the field by simultaneously estimating both the mean and covariance of LLM parameters within a single fine-tuning stage, leading to substantial performance improvements. Our proposed training-free Bayesianization represents a significant departure from these existing methods. Unlike approaches that require re-training ( Gal & Ghahramani 2016 ; Wang et al. 2023 ; Balabanov & Linander 2024 ; Wang et al. 2024d ) or rely on continued training and gradient estimation ( Yang et al. 2023 ) , our method achieves uncertainty estimation without any additional training steps, substantially improving the simplicity and efficiency for Bayesian learning of LLMs.


## 3 Methodology

In this section, we present Training-Free Bayesianization ( TFB ), detailing our approach across four subsections. Sec. 3.1 establishes the foundational problem setting and preliminaries. Sec. 3.2 introduces our low-rank isotropic Gaussian posterior formulation, while Sec. 3.3 presents our core contribution: a novel approach for converting deterministic weights to probabilistic distributions without training. Sec. 3.4 provides the complete algorithmic implementation. The theoretical foundations supporting our method are separately addressed in Sec. 4 .


## 3.1 Preliminaries

Low-Rank Adapation (LoRA). Given a pre-trained neural network layer with weight matrix 𝑾 0 {\bm{W}}_{0} , Low-Rank Adaptation (LoRA) ( Hu et al. 2022 ) confines weight updates to a low-rank subspace during fine-tuning, expressing the update as Δ ​ 𝑾 = 𝑩 ​ 𝑨 \Delta{\bm{W}}={\bm{B}}{\bm{A}} , where Δ ​ 𝑾 ∈ ℝ m × n \Delta{\bm{W}}\in\mathbb{R}^{m\times n} , 𝑩 ∈ ℝ m × r {\bm{B}}\in\mathbb{R}^{m\times r} , and 𝑨 ∈ ℝ r × n {\bm{A}}\in\mathbb{R}^{r\times n} . For input 𝒉 {\bm{h}} and output 𝒛 {\bm{z}} of the LoRA layer, the forward pass computation is given by:

LoRA Bayesianization with Degenerate Gaussian. BLoB ( Wang et al. 2024d ) , a pioneering work in low-rank Bayesianization for LLMs, empirically demonstrates that applying Gaussian distributions independently to elements of 𝑨 {\bm{A}} suffices for effective uncertainty estimation in LoRA. Specifically, each element follows q ⁡ ( A i ​ j ) = 𝒩 ⁡ ( A i ​ j | M i ​ j , Ω i ​ j 2 ) , ∀ i ∈ [ r ] , ∀ j ∈ [ n ] q(A_{ij})={\mathcal{N}}(A_{ij}|M_{ij},\Omega_{ij}^{2}),\forall i\in[r],\forall j\in[n] , where matrices 𝑴 {\bm{M}} and 𝛀 {\bm{\Omega}} , sharing the dimensions of 𝑨 {\bm{A}} , represent the mean and standard deviation of the random variable 𝑨 {\bm{A}} , respectively. This formulation yields a low-rank degenerate structure in the full-weight space for the Bayesianized low-rank adapter’s Gaussian posterior:

where 𝝁 q = vec ⁡ ( 𝑾 0 + 𝑩 ​ 𝑴 ) {\bm{\mu}}_{q}=\operatorname{vec}({\bm{W}}_{0}+{\bm{B}}{\bm{M}}) denotes the mean, and 𝚺 q = [ 𝑰 n ⊗ 𝑩 ] ​ [ diag ⁡ ( vec ⁡ ( 𝛀 ) 2 ) ] ​ [ 𝑰 n ⊗ 𝑩 ⊤ ] {\bm{\Sigma}}_{q}=[{\bm{I}}_{n}\otimes{\bm{B}}][\operatorname{diag}(\operatorname{vec}({\bm{\Omega}})^{2})][{\bm{I}}_{n}\otimes{\bm{B}}^{\top}] represents the low-rank degenerate covariance matrix.

In this work, we adopt a similar approach for modeling the variational distribution of the weight posterior by employing a Gaussian distribution with a low-rank degenerate covariance matrix, focusing exclusively on Bayesianizing the weight update matrix 𝑨 {\bm{A}} .


## 3.2 Low-Rank Isotropic Gaussian Posterior

Variational Distribution Family. In TFB , we constrain the variational distributions of the weight posterior to a more compact family of Gaussians than BLoB: specifically, we employ full-space isotropic Gaussian distributions projected onto the low-rank space:

where 𝝁 q {\bm{\mu}}_{q} is defined as in Eqn. 2 . Here, σ q 2 ​ 𝑰 ∈ ℝ m ​ n × m ​ n \sigma_{q}^{2}{\bm{I}}\in\mathbb{R}^{mn\times mn} represents a full-rank isotropic covariance matrix with standard deviation σ q \sigma_{q} , and proj \operatorname{proj} denotes a linear projection operator that maps the full-space covariance matrix onto the low-rank space jointly defined by 𝑩 {\bm{B}} and 𝑨 {\bm{A}} .

The choice of low-rank isotropic Gaussian posteriors serves both theoretical and empirical purposes: it provides a single-parameter family that enables converting the VI objective into a maximization problem (Sec. 3.3 and Theorem 4.2 ), and empirically outperforms alternative distribution families (Sec. 5.3 ). We now present a practically efficient implementation for Bayesianizing LoRA under the constraint specified in Eqn. 3 , with detailed theoretical analysis provided in Theorem 4.1 .

TFB in Practice. Consider a LoRA layer with weight updates 𝑩 ∈ ℝ m × r , 𝑨 ∈ ℝ r × n {\bm{B}}\in\mathbb{R}^{m\times r},{\bm{A}}\in\mathbb{R}^{r\times n} and a standard deviation scale σ q > 0 \sigma_{q}>0 . We begin by computing the compact Singular Value Decomposition (SVD) ( Klema & Laub 1980 ) of 𝑩 {\bm{B}} :

where 𝑼 ∈ ℝ m × r {\bm{U}}\in\mathbb{R}^{m\times r} and 𝑽 ∈ ℝ r × r {\bm{V}}\in\mathbb{R}^{r\times r} are orthonormal matrices, and 𝑫 = diag ⁡ ( 𝒅 ) ∈ ℝ r × r {\bm{D}}=\operatorname{diag}({\bm{d}})\in\mathbb{R}^{r\times r} is a diagonal matrix with positive entries 1 1 1 By stating 𝒅 ≻ 𝟎 {\bm{d}}\succ{\bm{0}} , we assume the original 𝑩 {\bm{B}} has the full column rank r r , which is usually the case for LLM adaptation (even for random initialization). . We then transform the original weight matrices { 𝑩 , 𝑨 } \{{\bm{B}},{\bm{A}}\} into an equivalent pair

maintaining the equality Δ ​ 𝑾 = 𝑩 ​ 𝑨 = 𝑩 ′ ​ 𝑨 ′ \Delta{\bm{W}}={\bm{B}}{\bm{A}}={\bm{B}}^{\prime}{\bm{A}}^{\prime} . Following BLoB’s Asymmetric Bayesianization scheme, we define the variational distribution for 𝑨 ′ {\bm{A}}^{\prime} using mean matrix 𝑴 = 𝑨 ′ {\bm{M}}={\bm{A}}^{\prime} and standard deviation matrix 𝛀 ∈ ℝ r × n {\bm{\Omega}}\in\mathbb{R}^{r\times n} , such that q ⁡ ( A i ​ j ′ ) = 𝒩 ⁡ ( A i ​ j ′ | M i ​ j , Ω i ​ j 2 ) , ∀ i ∈ [ r ] , ∀ j ∈ [ n ] q(A^{\prime}_{ij})={\mathcal{N}}(A^{\prime}_{ij}|M_{ij},\Omega_{ij}^{2}),\forall i\in[r],\forall j\in[n] . Unlike BLoB, our 𝛀 {\bm{\Omega}} is not freely parameterized but instead derived from projecting the full-space matrix σ q ​ 𝑰 \sigma_{q}{\bm{I}} onto the low-rank weight space:

This solution can be expressed compactly as 𝛀 = [ 1 / 𝒅 , ⋯ , 1 / 𝒅 ] {\bm{\Omega}}=[\nicefrac{{1}}{{{\bm{d}}}},\cdots,\nicefrac{{1}}{{{\bm{d}}}}] , comprising n n repeated vectors. This formulation significantly improves memory efficiency during inference, reducing the storage requirements for standard deviation parameters from O ⁡ ( r ​ n ) O(rn) to O ⁡ ( r ) O(r) . While alternative parameterization approaches are possible, they must be capable of generating the low-rank isotropic Gaussian noises as demonstrated in Theorem 4.1 . We have selected the current method to ensure maximum compatibility with existing implementations ( Wang et al. 2024d ) . In TFB , we maintain a single shared σ q \sigma_{q} across all LoRA layers.


## 3.3 Training-Free Bayesianization ( TFB )

The previous section presents a straightforward Bayesianization scheme for cases where the variational distribution of the full-weight matrix 𝑾 0 + Δ ​ 𝑾 {\bm{W}}_{0}+\Delta{\bm{W}} is constrained to the isotropic Gaussian family, assuming a predetermined value of σ q \sigma_{q} . In this section, we describe a practical method for determining σ q \sigma_{q} .

A General Bayesianization Framework. Consider an in-distribution “anchor” dataset 𝒟 {\mathcal{D}} , an associated evaluation metric l l , and a permissible performance degradation threshold ϵ \epsilon . Training-Free Bayesianization ( TFB ) formulates this as a constrained optimization problem:

where l ⁡ ( 𝒟 | 𝑩 ′ , 𝑴 , 𝛀 ⁡ ( σ q ) ) = 𝔼 𝑬 ∼ 𝒩 ⁡ ( 0 , 𝛀 ) ​ [ l ⁡ ( 𝒟 | 𝑩 ′ , 𝑴 + 𝑬 ) ] l({\mathcal{D}}|{\bm{B}}^{\prime},{\bm{M}},{\bm{\Omega}}(\sigma_{q}))=\mathbb{E}_{{\bm{E}}\sim{\mathcal{N}}(0,{\bm{\Omega}})}[l({\mathcal{D}}|{\bm{B}}^{\prime},{\bm{M}}+{\bm{E}})] represents the post-Bayesianization performance. This optimization seeks to maximize the noise scale σ q \sigma_{q} applied to model parameters 𝑴 {\bm{M}} while ensuring that the resulting performance degradation (or loss increase) remains within the acceptable threshold ϵ \epsilon .

Anchor Dataset 𝒟 {\mathcal{D}} and Evaluation Metric l l . The framework of TFB accommodates various choices of anchor dataset 𝒟 {\mathcal{D}} and evaluation metric l l based on practical requirements. We consider two key scenarios (with N N being slightly overloaded in its notation):

For supervised dataset 𝒟 = { 𝐱 n , y n } n = 1 N {\mathcal{D}}=\{{\bm{x}}_{n},y_{n}\}_{n=1}^{N} : The Negative-Log Likelihood (NLL) serves as a natural evaluation metric: l nll ( 𝒟 ) = − 1 N ∑ n = 1 N log P 𝜽 ( y n | 𝒙 n ) l_{\text{nll}}({\mathcal{D}})=-\tfrac{1}{N}\sum_{n=1}^{N}\log P_{\bm{\theta}}(y_{n}|{\bm{x}}_{n}) , as it directly corresponds to minimizing the variational free energy, as we demonstrate in Sec. 4 . The anchor dataset 𝒟 {\mathcal{D}} can be either the original training set used for the LoRA model or an independent calibration dataset, as commonly employed in calibration-based methods ( Guo et al. 2017 ; Zhao et al. 2021 ) . Alternative evaluation metrics such as accuracy or F1 score are also readily applicable. In our experimental setup, to ensure fair comparisons across uncertainty estimation baselines, we use the original training data as 𝒟 {\mathcal{D}} (maintaining the same information access as baselines) and employ accuracy as the evaluation metric.

For unsupervised dataset 𝒟 = { 𝐱 n } n = 1 N {\mathcal{D}}=\{{\bm{x}}_{n}\}_{n=1}^{N} : Our framework offers substantial flexibility compared to pure calibration methods. One approach is to generate pseudo-labels y ^ \widehat{y} using the model before Bayesianization, effectively converting the problem to the supervised case with 𝒟 = { 𝒙 n , y ^ n } n = 1 N {\mathcal{D}}=\{{\bm{x}}_{n},\widehat{y}_{n}\}_{n=1}^{N} . Additionally, the framework supports alternative evaluation metrics and statistical measures specifically designed for unsupervised data.

Performance Change Tolerance ϵ \epsilon . The selection of performance change tolerance ϵ \epsilon is critical in TFB . While our experiments demonstrate that a fixed ϵ = 1 % \epsilon=1\% for the accuracy metric achieves effective uncertainty estimation across various datasets and LoRA checkpoints (Table 8 ), an adaptive ϵ \epsilon can further enhance the performance of TFB (Table 1 ).

Many factors can affect the setting of ϵ \epsilon , among which the most important is the property of the given LoRA checkpoint. For instance, an overfitted LoRA can typically accommodate a larger tolerance ϵ \epsilon when using the training dataset (or its subset) as the anchor dataset. Additional characteristics of the data, model, and adaptation tasks can also inform the choice of ϵ \epsilon . For simplicity and reproducibility in this work, we consider only a binary indicator of LoRA overfitting (which can be readily assessed through ECE when a small validation set is available). We set ϵ = 1 % \epsilon=1\% for overfitted LoRAs and ϵ = 0.5 % \epsilon=0.5\% for others as the maximum acceptable accuracy degradation.


## 3.4 TFB : Final Algorithm

Our final algorithm, presented in Algorithm 1 , employs a search strategy to determine the optimal σ q ∗ \sigma_{q}^{*} within an initial range [ σ q min , σ q max ] [{\sigma_{q}}_{\text{min}},{\sigma_{q}}_{\text{max}}] . While binary search would guarantee the optimal solution, we opt for a more efficient parallel approach in practice: we conduct a grid search across 8 different σ q \sigma_{q} values in parallel, construct an approximate function σ ^ q ​ ( p ) \widehat{\sigma}_{q}(p) through piecewise linear interpolation of the observed performance, and estimate σ q ∗ ≈ σ ^ q ​ ( p 0 − ϵ ) \sigma_{q}^{*}\approx\widehat{\sigma}_{q}(p_{0}-\epsilon) , where p 0 p_{0} denotes the model’s performance before TFB .

After identifying the optimal σ q ∗ \sigma_{q}^{*} , we Bayesianize all LoRA layers using this value. For prediction, we sample multiple times from the weight posterior and average the output:

where q ⁡ ( 𝑾 | 𝜽 ) q({\bm{W}}|{\bm{\theta}}) denotes the variational distribution defined in Eqn. 3 , and we set the number of test-time samples to N = 10 N=10 , following BLoB’s protocol ( Wang et al. 2024d ) .


## 4 Theoretical Analysis

We present our theoretical analysis in this section (with complete proofs provided in Appendix A ). First, we demonstrate that our Bayesianization scheme, defined in Equations 4 , 5 , and 6 , projects a full-rank isotropic Gaussian distribution onto the low-rank space. We then prove that optimizing Eqn. 7 is equivalent to performing variational inference for LLM’s weights under specific, achievable conditions.

The evaluation metric l 𝒟 : ℝ + → ℝ + l_{\mathcal{D}}:\mathbb{R}_{+}\rightarrow\mathbb{R}_{+} is the Negative Log Likelihood (NLL) evaluated on the data distribution 𝒟 {\mathcal{D}} for the given posterior standard deviation σ q \sigma_{q} :

Furthermore, we assume l 𝒟 l_{\mathcal{D}} is locally convex, i.e., there exists ϵ 0 > 0 \epsilon_{0}>0 such that l 𝒟 ′′ ​ ( σ q ) > 0 l_{\mathcal{D}}^{\prime\prime}(\sigma_{q})>0 , for all σ q ∈ [ 0 , ϵ 0 ) \sigma_{q}\in[0,\epsilon_{0}) .

The local convexity of the loss function is not an unrealistic assumption ( Milne 2019 ) . For instance, a local minimum 𝐖 0 {\bm{W}}_{0} of a twice-differentiable loss function l l will imply the local convexity around 𝐖 0 {\bm{W}}_{0} , which has been widely assumed in Laplace Approximation ( Tierney & Kadane 1986 ; Bishop 2006 ) .

With the pre-trained weight matrix 𝐖 0 ∈ ℝ m × n {\bm{W}}_{0}\in\mathbb{R}^{m\times n} , the low-rank weight update matrix { 𝐁 ′ ∈ ℝ m × r , 𝐀 ′ ∈ ℝ r × n } \{{\bm{B}}^{\prime}\in\mathbb{R}^{m\times r},{\bm{A}}^{\prime}\in\mathbb{R}^{r\times n}\} transformed from the given matrices { 𝐁 , 𝐀 } \{{\bm{B}},{\bm{A}}\} following Eqn. 4 and 5 , suppose that the variational distribution of 𝐀 ′ {\bm{A}}^{\prime} is Gaussian q ⁡ ( 𝐀 ′ | 𝛉 ) = ∏ i ​ j 𝒩 ⁡ ( A i ​ j | M i ​ j , Ω i ​ j 2 ) q({\bm{A}}^{\prime}|{\bm{\theta}})=\prod_{ij}{\mathcal{N}}(A_{ij}|M_{ij},\Omega_{ij}^{2}) , where 𝐌 = [ M i ​ j = A i ​ j ′ ] ∈ ℝ r × n {\bm{M}}=[M_{ij}=A^{\prime}_{ij}]\in\mathbb{R}^{r\times n} is its mean and 𝛀 = [ Ω i ​ j ] ∈ ℝ r × n {\bm{\Omega}}=[\Omega_{ij}]\in\mathbb{R}^{r\times n} is the standard deviation calculated as in Eqn. 6 . The equivalent variational distribution q ⁡ ( vec ⁡ ( 𝐖 ) | σ q ) q(\operatorname{vec}({\bm{W}})|\sigma_{q}) defined on the full weight matrix is

Theorem 4.1 establishes that for any given σ q \sigma_{q} , our algorithm for regrouping 𝑩 , 𝑨 {\bm{B}},{\bm{A}} and computing the standard deviation matrix 𝛀 {\bm{\Omega}} successfully constrains the corresponding full-weight variational distributions to the family of low-rank isotropic Gaussian distributions. While alternative families of Gaussian distributions parameterized by a single scale σ q \sigma_{q} are possible, our empirical results demonstrate that our proposed approach achieves superior performance (Sec. 5.3 ).

Suppose the evaluation metric l 𝒟 ​ ( σ q ) l_{\mathcal{D}}(\sigma_{q}) defined following Assumption 4.1 is locally convex within the range of σ q ∈ [ 0 , ϵ 0 ) \sigma_{q}\in[0,\epsilon_{0}) . Suppose the posterior distribution of 𝐖 {\bm{W}} given σ q \sigma_{q} is defined following Theorem 4.2 . Suppose we have the prior distribution P ⁡ ( vec ⁡ ( 𝐖 ) ) = 𝒩 ⁡ ( vec ⁡ ( 𝐖 ) | 𝛍 p , 𝚺 p ) P(\operatorname{vec}({\bm{W}}))={\mathcal{N}}(\operatorname{vec}({\bm{W}})|{\bm{\mu}}_{p},{\bm{\Sigma}}_{p}) , where 𝛍 p = 𝛍 q = vec ⁡ ( 𝐖 0 + 𝐁 ′ ​ 𝐌 ) {\bm{\mu}}_{p}={\bm{\mu}}_{q}=\operatorname{vec}({\bm{W}}_{0}+{\bm{B}}^{\prime}{\bm{M}}) , and 𝚺 p = σ p 2 ​ 𝐈 {\bm{\Sigma}}_{p}=\sigma_{p}^{2}{\bm{I}} with σ p ≫ ϵ 0 \sigma_{p}\gg\epsilon_{0} . Then ∃ ϵ > 0 \exists\epsilon>0 , s.t. the following two optimizations

(i) Minimization of Variational Free-Energy ( Blundell et al. 2015 )

and (ii) Training-Free Bayesianization ( TFB )

are equivalent, where λ \lambda is the coefficient of the KL-divergence regularization.

This theorem provides the primary theoretical foundation for our approach. It demonstrates that under specific conditions—namely, local convexity within [ 0 , ϵ 0 ) [0,\epsilon_{0}) and prior standard deviation σ p ≫ ϵ 0 \sigma_{p}\gg\epsilon_{0} —maximizing the scale σ q \sigma_{q} of the standard deviation matrix is equivalent to minimizing the variational free energy, which corresponds to performing variational inference for the weight posterior distribution.

TFB maintains theoretical soundness (through its equivalence to Variational Inference (VI)) while offering practical simplicity, as it eliminates the need to explicitly specify the prior distribution’s standard deviation σ p \sigma_{p} . The condition σ p ≫ ϵ 0 \sigma_{p}\gg\epsilon_{0} is naturally satisfied by common choices such as the standard normal distribution ( σ p = 1 \sigma_{p}=1 ) or uniform distribution ( σ p → + ∞ \sigma_{p}\rightarrow+\infty ).


## 5 Experiments

In this section, we evaluat TFB through comprehensive experiments on various settings. Sec. 5.1 details our experimental setup, including baselines and evaluation protocols. We then present our main results on in- and out-of-distribution performance in Sec. 5.2 , followed by an ablation study analyzing key components of our method in Sec. 5.3 . To demonstrate the broad applicability of our approach, we conduct additional experiments on different LLM architectures (Sec. 5.4 ) and explore its compatibility with other LoRA-like PEFT methods (Sec. 5.5 ).


## 5.1 Settings

Models, Datasets, and Evaluation. Following prior work on Bayesian low-rank adaptation ( Yang et al. 2023 ; Wang et al. 2023 ; Wang et al. 2024d ) , we use llama-2-7b-hf as our primary LLM backbone. We provide additional results on recent LLM architectures in Sec. 5.4 , including Meta-Llama-3-8B , Meta-Llama-3.1-8B , and Mistral-7B-v0.3 from the Llama ( Dubey et al. 2024 ) and Mistral ( Jiang et al. 2023 ) families.

For in-distribution experiments, we evaluate model performance on six commonsense reasoning tasks: Winogrande-Small ( WG-S ) and Winogrande-Medium ( WG-M ) ( Sakaguchi et al. 2021 ) , ARC-Challenge ( ARC-C ) and ARC-Easy ( ARC-E ) ( Clark et al. 2018 ) , Open Book Question Answering ( OBQA ) ( Mihaylov et al. 2018 ) , and BoolQ ( Clark et al. 2019 ) . Furthermore, we use models fine-tuned on OBQA ( Mihaylov et al. 2018 ) to evaluate their generalization ability on out-of-distribution datasets: college-level chemistry ( Chem ) and physics ( Phy ) subsets of MMLU ( Hendrycks et al. 2021 ) . Label spaces and prompt templates are detailed in Appendix B.1 .

To assess uncertainty estimation, we measure Expected Calibration Error ( ECE ( Naeini et al. 2015 ) ) and Negative Log-Likelihood ( NLL ) on the test dataset. We also report Accuracy ( ACC ) to ensure models maintain strong performance while improving calibration. Additional evaluation details are provided in Appendix B.2 .

Baselines. We compare TFB with state-of-the-art uncertainty estimation methods for LoRA-adapted LLMs, including ensemble-based method: Deep Ensemble ( ENS ) ( Lakshminarayanan et al. 2017 ; Balabanov & Linander 2024 ; Wang et al. 2023 ) , variational inference methods: Monte-Carlo Dropout ( MCD ) ( Gal & Ghahramani 2016 ) , Bayes By Backprop ( BBB ) ( Blundell et al. 2015 ) , Bayesian LoRA by Backprop ( BLoB ) ( Wang et al. 2024d ) , and post-training method: Laplace-LoRA ( LAP ) ( Yang et al. 2023 ) . For reference, we also include two standard PEFT baselines: Maximum Likelihood Estimation ( MLE ) ( Hu et al. 2022 ) and Maximum A Posteriori ( MAP ). All baselines are implemented following the protocols established in BLoB, with details provided in Appendix B .

TFB Implementation. TFB requires no training and can be directly applied to trained LoRA adapters. We evaluate it on three off-the-shelf LoRA checkpoints: MLE , MAP , and the mean component of BLoB (obtained by discarding BLoB’s standard deviation matrix 𝛀 {\bm{\Omega}} ). For implementation, we use accuracy as the evaluation metric l l and randomly sample a subset of the training data as the anchor dataset 𝒟 {\mathcal{D}} (for the size of each dataset, refer to Appendix B.1 ). The performance change tolerance ϵ \epsilon is set adaptively to either 1% or 0.5%, depending on the checkpoint’s overfitting characteristics. To determine the optimal σ q ∗ \sigma_{q}^{*} , we conduct parallel experiments with eight values of σ q ∈ \sigma_{q}\in [0.01, 0.015, 0.02, 0.025, 0.03, 0.035, 0.04, 0.05] using a single random seed. We construct an approximate function σ ^ q ​ ( p ) \widehat{\sigma}_{q}(p) through piecewise linear interpolation of the observed performance and estimate σ q ∗ ≈ σ ^ q ​ ( p 0 − ϵ ) \sigma_{q}^{*}\approx\widehat{\sigma}_{q}(p_{0}-\epsilon) . Similar to other baseline methods, the final results of TFB are reported as averages across three random seeds using σ q ∗ \sigma_{q}^{*} .


## 5.2 TFB Improves Accuracy and Uncertainty Estimation Across Distributional Shifts

Table 1 presents comprehensive performance metrics (ACC, ECE, and NLL) for various methods applied to LoRA on Llama2-7B pre-trained weights. Due to space limitations, we report the full empirical results of TFB variants (with different ϵ \epsilon s) in Appendix C.1 .

In-Distribution Results. Looking at the IND Datasets results, several key patterns emerge. The MLE baseline shows relatively strong accuracy but suffers from high ECE values (e.g., 29.83 on WG-S), indicating significant overconfidence. This aligns with the common challenge of LLM overconfidence during conventional fine-tuning.

TFB applied to BLoB-Mean demonstrates strong overall performance across the IND datasets, achieving the highest accuracy on several datasets (69.94 on WG-S, 70.72 on ARC-C, and 86.74 on ARC-E). More importantly, it achieves this while maintaining lower ECE values compared to methods like MCD and ENS, suggesting better calibrated predictions. The method also shows strong NLL performance, with values consistently among the lowest across datasets (0.62 for WG-S, 0.86 for ARC-C).

In summary, TFB consistently enhances the performance of baseline methods (MLE, MAP, and BLoB-Mean) across different evaluation scenarios, with notable improvements in both accuracy and calibration metrics. The improvements are particularly evident in the significant ECE reductions (e.g., from 29.83 to 16.26 for MLE on WG-S) while maintaining or improving accuracy, with the most substantial gains observed when TFB is combined with BLoB-Mean, achieving both the highest accuracy and lowest ECE values across most datasets.

Out-of-Distribution Results. The OOD evaluation reveals interesting patterns across both smaller and larger distribution shifts. For smaller shifts (ARC-C and ARC-E), BLoB-Mean with TFB maintains strong performance, achieving 70.38 and 80.16 accuracy respectively, while keeping ECE values low (12.28 and 8.07). This suggests robust generalization under moderate distribution shifts.

For larger shifts (Chem and Phy datasets), we see a more significant performance degradation across all methods, as expected. However, BLoB-Mean with TFB still maintains competitive performance, achieving 42.67 accuracy on Chem and 30.67 on Phy, while maintaining reasonable calibration metrics. The method’s NLL values (1.35 and 1.46 respectively) remain competitive with other approaches, indicating relatively well-calibrated uncertainty estimates even under substantial distribution shifts.

Notable is the consistently strong performance of the BLoB variants (both w/ and w/o TFB ) across different metrics and datasets, suggesting that this approach offers a robust framework for both in-distribution and out-of-distribution scenarios. The results demonstrate that the method successfully balances the trade-off between accuracy and calibration, particularly evident in the OOD scenarios where maintaining both aspects becomes more challenging.


## 5.3 TFB Beyond Low-Rank Isotropic Gaussians

In this section, we extend TFB to other families of Gaussians for modeling the variational distributions of 𝑾 {\bm{W}} . Specifically, we consider: (i) Full-Rank Isotropic Gaussian ( FR , 𝚺 q = σ q 2 ​ 𝑰 {\bm{\Sigma}}_{q}=\sigma_{q}^{2}{\bm{I}} ), and (ii) Constant Low-Rank Standard Deviation ( C-STD , 𝛀 = [ Ω i ​ j = σ q ] {\bm{\Omega}}=[\Omega_{ij}=\sigma_{q}] ). For fair comparison, we adopt the same optimal σ q ∗ \sigma_{q}^{*} search protocol of TFB as decribed in Sec. 5.1 . The performances of TFB and its variants applied to the mean of BLoB are reported in Table 2 .

The experimental results show that TFB outperforms both the baselines FR and C-STD across multiple metrics on in-distribution datasets, with notable improvements in accuracy (e.g., OBQA: 83.13) and calibration (ECE reduced by up to 16.74). While the baseline methods show better NLL scores, these improvements come at the cost of significantly degraded overall performance, making them impractical for real-world applications. While it maintains strong performance on datasets with smaller distributional shifts, its advantages diminish on datasets with larger shifts in Physics and Chemistry domains.

Advantages of TFB . TFB offers additional advantages over the other families of variational distributions discussed above. It is computationally more efficient than FR with noise complexity of O ⁡ ( r ​ n ) O(rn) versus O ⁡ ( m ​ n ) O(mn) . Furthermore, unlike C-STD whose variational distributions vary with different but equivalent LoRA matrix pairs and can potentially break the conditions in Theorem 4.2 (Appendix C.2 ), TFB produces consistent Bayesianization for all equivalent LoRAs satisfying 𝑩 ​ 𝑨 = Δ ​ 𝑾 {\bm{B}}{\bm{A}}=\Delta{\bm{W}} .


## 5.4 TFB Beyond the Llama2-7B Backbone

We conduct comprehensive experiments across multiple LLM backbones to validate our approach. Our experiments span several models from the Llama architecture ( Touvron et al. 2023b ; Dubey et al. 2024 ) , including llama-2-7b-hf , Meta-Llama-3-8B , and Meta-Llama-3.1-8B . While we initially considered Llama-3.2-1B , we ultimately discarded its results due to poor adaptation performance with the smaller model architecture. We also extend our analysis to include Mistral-7B-v0.3 ( Jiang et al. 2023 ) .

Following commonsense-170k ( Hu et al. 2023 ; Wang et al. 2024c ) , we combine the 6 reasoning sub-tasks from the main experiments with one shared label space ( Combined ) and train the base LoRA adapters with MLE. Break-down statistics of each sub-dataset are available in Appendix C.3 . For TFB , we set the variational posterior’s standard deviation to σ q = \sigma_{q}= 1e-3 for all three Llama models, while using a lower value of σ q = \sigma_{q}= 2e-3 for Mistral-7B-v0.3 .

The results shown in Table 3 demonstrate TFB ’s effectiveness: it dramatically reduces ECE across all models (e.g., from 4.74 to 1.05 for Llama3.1-8B) while maintaining strong accuracy and NLL scores with minimal degradation.


## 5.5 TFB Beyond the Naive LoRA

Our proposed TFB is compatible with various LoRA-based methods that use different initialization strategies ( Meng et al. 2024 ) , parameter sharing schemes ( Kopiczko et al. 2023 ) , and optimization approaches ( Zhang et al. 2023 ) . We evaluate TFB on two representative LoRA variants:

VeRA ( Kopiczko et al. 2023 ) : Uses shared low-rank matrices 𝑩 {\bm{B}} and 𝑨 {\bm{A}} across layers, with layer-specific trainable scalar vector 𝒅 {\bm{d}} and bias vector 𝒃 {\bm{b}} .

PiSSA ( Meng et al. 2024 ) : Employs an alternative initialization while maintaining LoRA’s training process.

We conduct experiments on Llama-3.1-8B following the protocol described in Sec. 5.4 . Detailed results for individual datasets and the technical adaptations required to satisfy the assumptions in Eqn. 3 (variational distribution to be a low-rank isotropic Gaussian) for each LoRA variant are provided in Appendix C.4 .

The results in Table 4 demonstrate TFB ’s broad applicability: it substantially reduces ECE across all LoRA-like PEFT methods (e.g., from 5.11 to 1.44 for VeRA). Importantly, it maintains strong ACC and NLL scores with minimal performance degradation, validating the effectiveness of low-rank isotropic Gaussian distribtuions for variational inference of LLMs.


## 5.6 Improving the Efficiency of TFB

Inspired by Harrison et al. 2024 , we adopt last-layer Bayesianization to increase the inference speed. In our approach, we employ the same prior standard deviation σ q \sigma_{q} as identified through full-model Bayesian tuning, but restrict the Bayesian treatment to the last layer of model. By limiting inference to sampling from the posterior distribution of the last layer, the outputs of earlier layers can be reused, significantly improving inference speed. Although restricting Bayesianization to the last layer sacrifices some ability to effectively model uncertainty across the entire model, this approach allows for a higher number of posterior samples, resulting in more accurate approximations.

As shown in Table 5 , when only N = 10 N=10 samples are used, the uncertainty estimation of last-layer Bayesianization performs worse than that of full-model Bayesianization. Nevertheless, the improved posterior estimation with N = 100 N=100 samples enables last-layer Bayesianization to achieve better performance. For a comprehensive analysis of its performance, please refer to Appendix C.5 .


## 6 Conclusion

In this paper, we introduce Training-Free Bayesianization ( TFB ), a novel framework that transforms trained LoRA adapters into Bayesian ones without additional training. By systematically searching for the maximally acceptable variance in the weight posterior within a family of low-rank isotropic Gaussian distributions, TFB provides a practical solution to uncertainty estimation in LLMs. We theoretically demonstrate that TFB ’s variance maximization process is equivalent to variational inference under mild conditions, while empirically showing its superior performance across various settings and model configurations. Our framework’s simplicity and effectiveness, requiring only an anchor dataset for search, makes it widely applicable across different domains. As LLMs continue to evolve, TFB represents a significant step toward more reliable and uncertainty-aware AI systems, paving the way for future research in adaptive and trustworthy machine learning.


## 7 Limitations

TFB is subject to several limitations. First, our approach relies on the availability of an anchor dataset for determining search range and stopping criteria. Although this dataset doesn’t require supervision or prior use in LoRA training, its quality and representativeness could impact the effectiveness of uncertainty estimation. Second, by constraining the family of full-weight posteriors to low-rank isotropic Gaussian distributions, TFB may not capture more complex uncertainty patterns that could be present in the data. While this constraint enables our training-free approach, it represents a trade-off between computational efficiency and model expressiveness. Finally, while we have demonstrated the effectiveness of TFB in various settings, its performance in more complex generation tasks requires further investigation. Future work could explore extending the framework to handle more sophisticated language generation scenarios and broader applications.


## References


## Appendix

In Appendix A , we provide detailed proofs for all theorems presented in the main paper. In Appendix B , we describe our experimental methodology. Finally, in Appendix C , we present additional empirical results, including the full results of experiments with different searching strategies for optimal σ q ∗ \sigma_{q}^{*} , variational distribution family, LLM backbones, and LoRA-like PEFTs.


## Appendix A Proof of Theorems

With the pre-trained weight matrix 𝐖 0 ∈ ℝ m × n {\bm{W}}_{0}\in\mathbb{R}^{m\times n} , the low-rank weight update matrix { 𝐁 ′ ∈ ℝ m × r , 𝐀 ′ ∈ ℝ r × n } \{{\bm{B}}^{\prime}\in\mathbb{R}^{m\times r},{\bm{A}}^{\prime}\in\mathbb{R}^{r\times n}\} transformed from the given matrices { 𝐁 , 𝐀 } \{{\bm{B}},{\bm{A}}\} following Eqn. 4 and 5 , suppose that the variational distribution of 𝐀 ′ {\bm{A}}^{\prime} is Gaussian q ⁡ ( 𝐀 ′ | 𝛉 ) = ∏ i ​ j 𝒩 ⁡ ( A i ​ j | M i ​ j , Ω i ​ j 2 ) q({\bm{A}}^{\prime}|{\bm{\theta}})=\prod_{ij}{\mathcal{N}}(A_{ij}|M_{ij},\Omega_{ij}^{2}) , where 𝐌 = [ M i ​ j = A i ​ j ′ ] ∈ ℝ r × n {\bm{M}}=[M_{ij}=A^{\prime}_{ij}]\in\mathbb{R}^{r\times n} is its mean and 𝛀 = [ Ω i ​ j ] ∈ ℝ r × n {\bm{\Omega}}=[\Omega_{ij}]\in\mathbb{R}^{r\times n} is the standard deviation calculated as in Eqn. 6 . The equivalent variational distribution q ⁡ ( vec ⁡ ( 𝐖 ) | σ q ) q(\operatorname{vec}({\bm{W}})|\sigma_{q}) defined on the full weight matrix 𝐖 {\bm{W}} is

We have the following lemma from BLoB that calculates the covariance matrix of a given low-rank Bayesianization scheme { 𝑩 , 𝑨 , 𝛀 } \{{\bm{B}},{\bm{A}},{\bm{\Omega}}\} ( Wang et al. 2024d ) .

With the pre-trained weight matrix 𝐖 0 ∈ ℝ m × n {\bm{W}}_{0}\in\mathbb{R}^{m\times n} and the low-rank weight update matrix 𝐁 ∈ ℝ m × r {\bm{B}}\in\mathbb{R}^{m\times r} , suppose that the variational distribution of the other low-rank update matrix 𝐀 ∈ ℝ r × n {\bm{A}}\in\mathbb{R}^{r\times n} is Gaussian with q ⁡ ( 𝐀 | 𝛉 = { 𝐌 , 𝛀 } ) = ∏ i ​ j 𝒩 ⁡ ( A i ​ j | M i ​ j , Ω i ​ j 2 ) q({\bm{A}}|{\bm{\theta}}=\{{\bm{M}},{\bm{\Omega}}\})=\prod_{ij}{\mathcal{N}}(A_{ij}|M_{ij},\Omega_{ij}^{2}) , where 𝐌 = [ M i ​ j ] ∈ ℝ r × n {\bm{M}}=[M_{ij}]\in\mathbb{R}^{r\times n} and 𝛀 = [ Ω i ​ j ] ∈ ℝ r × n {\bm{\Omega}}=[\Omega_{ij}]\in\mathbb{R}^{r\times n} are its mean and standard deviation, respectively. The equivalent variational distribution defined on the full weight matrix 𝐖 {\bm{W}} is given by

Based on the assumption outlined in Eqn. 4 , 5 , and 6 , we have the following properties about 𝑩 ′ {\bm{B}}^{\prime} , 𝑴 {\bm{M}} , and 𝛀 {\bm{\Omega}} of TFB :

It now can be easily shown that the covariance matrix of TFB is:

which proves that q ⁡ ( vec ⁡ ( 𝑾 ) ) q(\operatorname{vec}({\bm{W}})) is a low-rank isotropic Gaussian distribution. ∎

Suppose the evaluation metric l 𝒟 ​ ( σ q ) l_{\mathcal{D}}(\sigma_{q}) defined following Assumption 4.1 is locally convex within the range of 0 < σ q < ϵ 0 0<\sigma_{q}<\epsilon_{0} . Suppose the posterior distribution of 𝐖 {\bm{W}} given σ q \sigma_{q} is defined following Theorem 4.2 . Suppose we have the prior distribution P ⁡ ( vec ⁡ ( 𝐖 ) ) = 𝒩 ⁡ ( vec ⁡ ( 𝐖 ) | 𝛍 p , 𝚺 p ) P(\operatorname{vec}({\bm{W}}))={\mathcal{N}}(\operatorname{vec}({\bm{W}})|{\bm{\mu}}_{p},{\bm{\Sigma}}_{p}) , where 𝛍 p = 𝛍 q = vec ⁡ ( 𝐖 0 + 𝐁 ′ ​ 𝐌 ) {\bm{\mu}}_{p}={\bm{\mu}}_{q}=\operatorname{vec}({\bm{W}}_{0}+{\bm{B}}^{\prime}{\bm{M}}) , and 𝚺 p = σ p 2 ​ 𝐈 {\bm{\Sigma}}_{p}=\sigma_{p}^{2}{\bm{I}} with σ p ≫ ϵ 0 \sigma_{p}\gg\epsilon_{0} . Then ∃ ϵ > 0 \exists\epsilon>0 , s.t. the two following optimization problems

(i) Minimization of Variational Free-Energy ( Blundell et al. 2015 )

and (ii) Training-Free Bayesianization ( TFB )

are equivalent, where λ \lambda is the coefficient of the KL-divergence regularization.

First we prove the KL divergence term is convex w.r.t. σ q \sigma_{q} . For two Gaussian distributions q q and p p whose covariance matrices 𝚺 q ∈ ℝ d × d {\bm{\Sigma}}_{q}\in\mathbb{R}^{d\times d} and 𝚺 p ∈ ℝ d × d {\bm{\Sigma}}_{p}\in\mathbb{R}^{d\times d} are both full-rank, and their means as 𝝁 q ∈ ℝ d {\bm{\mu}}_{q}\in\mathbb{R}^{d} and 𝝁 p ∈ ℝ d {\bm{\mu}}_{p}\in\mathbb{R}^{d} , we have their KL-divergence as

For TFB , to avoid unbounded KL divergence, we project the original assumed Gaussian prior P P into the same low-rank sub-space of the posterior q q . We summarize the prior and variational distribution of the posterior as follows:

Substituting Eqn. 26 back into Eqn. 25 , we have

which is convex w.r.t. σ q \sigma_{q} and the global minimum of KL \operatorname{KL} is achieved when σ q = σ p \sigma_{q}=\sigma_{p} .

With σ q ≤ ϵ 0 \sigma_{q}\leq\epsilon_{0} , the convexity of two terms ( KL \operatorname{KL} and l 𝒟 l_{\mathcal{D}} ) holds. Hence we show by the Karush–Kuhn–Tucker theorem ( Kjeldsen 2000 ; Karush 1939 ; Kuhn & Tucker 1951 ) that the following two optimization problems are equivalent:

Minimization of Variational Free-Energy as the Lagrange-form optimization

The constrained-form optimization corresponding to Eqn. 28

Since the KL \operatorname{KL} term is monotonically decreasing when σ q ∈ [ 0 , σ p ) \sigma_{q}\in[0,\sigma_{p}) , and due to the fact that σ p > ϵ 0 \sigma_{p}>\epsilon_{0} , the optimization in Eqn. 29 is equivalent to:

Training-Free Bayesianization ( TFB )

∎


## Appendix B Implementation Details


## B.1 Datasets

We provide details of the datasets used in this work, as shown in Table 6 . The combined dataset consisting of the six commonsense reasoning tasks contains the label set of “[A, B, C, D, E, True, False]”.


## B.2 Evaluation Metrics

Negative Log-Likelihood ( NLL ) and Expected Calibration Error ( ECE ( Naeini et al. 2015 ) ) are key metrics for uncertainty estimation. For a model P 𝜽 P_{\bm{\theta}} and test dataset { 𝒙 n , y n } n = 1 N \{{\bm{x}}_{n},y_{n}\}_{n=1}^{N} , NLL penalizes models that assign low probabilities to correct labels, and is defined as:

ECE measures the alignment between model confidence and accuracy by binning predictions:

where acc ​ ( B m ) = 1 / | B m | ​ ∑ i ∈ B m 𝟙 ​ ( y ^ i = y i ) \text{acc}(B_{m})=\nicefrac{{1}}{{|B_{m}|}}\sum_{i\in B_{m}}\mathbbm{1}{(\widehat{y}_{i}=y_{i})} is the average accuracy and conf ​ ( B m ) = 1 / | B m | ​ ∑ i ∈ B m P ⁡ ( y ^ i ) \text{conf}(B_{m})=\nicefrac{{1}}{{|B_{m}|}}\sum_{i\in B_{m}}P(\widehat{y}_{i}) is the average confidence in bin B m B_{m} . We use bin size | B m | = 15 |B_{m}|=15 throughout our experiments.


## B.3 Optimal σ q ∗ \sigma_{q}^{*} of TFB Variants

TFB converts the end-to-end training using variational inference to a variance maximization problem. It is done through trimming down the set of trainable parameters to a single variable σ q \sigma_{q} . How to use this single variable σ q \sigma_{q} to define a better distribution family remains an intriguing problem for future research.

In Sec. 5.3 , to show more possibilities of such, we extend TFB to other families of Gaussians for modeling the variational distributions of 𝑾 {\bm{W}} . Specifically, we consider: (i) Full-Rank Isotropic Gaussian ( FR , 𝚺 q = σ q 2 ​ 𝑰 {\bm{\Sigma}}_{q}=\sigma_{q}^{2}{\bm{I}} ), and (ii) Constant Low-Rank Standard Deviation ( C-STD , 𝛀 = [ Ω i ​ j = σ q ] {\bm{\Omega}}=[\Omega_{ij}=\sigma_{q}] ).

For fair comparison, we adopt the same optimal σ q ∗ \sigma_{q}^{*} search protocol of TFB as decribed in Sec. 5.1 . In Table 7 , we show the optimal setting of σ q ∗ \sigma_{q}^{*} with adaptive performance change tolerance ϵ = 1 % \epsilon=1\% or ϵ = 0.5 % \epsilon=0.5\% searched for all three variational distribution families. Additionally, we show the upper-bound performance of each of them by directly tuning σ q \sigma_{q} on the test set, aiming to minimize the ECE.


## B.4 Training

We report the mean and standard deviation of all experimental results calculated over three random seeds. For all training processes in our experiments, we employ the AdamW optimizer. The learning rate follows a linear decay schedule with a warmup ratio of 0.06 and a maximum value of 1 ​ e − 4 1e-4 . The batch size is set to 4, and the maximum sentence length is limited to 300 tokens. Additionally, the LoRA configuration includes LoRA α = 16 \alpha=16 and LoRA r = 8 r=8 . PiSSA ( Meng et al. 2024 ) follows the exact same configuration as the LoRA’s. For VeRA ( Kopiczko et al. 2023 ) , due to its characteristic of shared weights across different layers, we set its rank r = 256 r=256 and learning rate to 5 ​ e − 3 5e-3 for the MLE training on the combined dataset.


## Appendix C Additional Experimental Results


## C.1 TFB Variants: ϵ \epsilon s and Optimal Calibration

In Table 1 (Sec. 5.2 ), we present TFB results using adaptive ϵ \epsilon (1% or 0.5%) based on LoRA’s overfitting status. Table 8 shows comprehensive results for both ϵ \epsilon values, along with an Optimal ECE where σ q \sigma_{q} is optimized on test data for best ECE. This bound demonstrates TFB ’s potential when a calibration dataset is available, though this reduces it to a degraded calibration method.


## C.2 TFB Beyond Low-Rank Isotropic Gaussians

In Table 2 (Sec. 5.3 ), we compare TFB with two alternative Gaussian distribution families that are controlled by a single parameter σ q \sigma_{q} :

Full-Rank Isotropic Gaussian ( FR ): given σ q \sigma_{q} , the FR’s variational distribution of the weight matrix q ⁡ ( vec ⁡ ( 𝑾 ) ) = 𝒩 ⁡ ( vec ⁡ ( 𝑾 ) | 𝝁 q , 𝚺 q ) q(\operatorname{vec}({\bm{W}}))={\mathcal{N}}(\operatorname{vec}({\bm{W}})|{\bm{\mu}}_{q},{\bm{\Sigma}}_{q}) where 𝝁 q = 𝑾 0 + 𝑩 ​ 𝑨 {\bm{\mu}}_{q}={\bm{W}}_{0}+{\bm{B}}{\bm{A}} (same as TFB ) and 𝚺 q = σ q 2 ​ 𝑰 m ​ n {\bm{\Sigma}}_{q}=\sigma_{q}^{2}{\bm{I}}_{mn} is full-rank.

Constant Standard Deviation Matrix ( C-STD ): given σ q \sigma_{q} , the C-STD’s variational distribution of the weight matrix q ⁡ ( vec ⁡ ( 𝑾 ) ) = 𝒩 ⁡ ( vec ⁡ ( 𝑾 ) | 𝝁 q , 𝚺 q ) q(\operatorname{vec}({\bm{W}}))={\mathcal{N}}(\operatorname{vec}({\bm{W}})|{\bm{\mu}}_{q},{\bm{\Sigma}}_{q}) where 𝝁 q = 𝑾 0 + 𝑩 ​ 𝑨 {\bm{\mu}}_{q}={\bm{W}}_{0}+{\bm{B}}{\bm{A}} (same as TFB ) and 𝚺 q = σ q 2 ⋅ 𝑰 n ⊗ [ 𝑩 ​ 𝑩 ⊤ ] {\bm{\Sigma}}_{q}=\sigma_{q}^{2}\cdot{\bm{I}}_{n}\otimes[{\bm{B}}{\bm{B}}^{\top}] .

C-STD’s covariance matrix 𝚺 q {\bm{\Sigma}}_{q} is derived through Lemma A.1 :

This depends on 𝑩 {\bm{B}} and thus varies for equivalent LoRA parameterizations 𝑩 , 𝑨 {{\bm{B}},{\bm{A}}} of the same Δ ​ 𝑾 \Delta{\bm{W}} .

Table 9 shows the optimal test-set ECE for all three distributions to eliminate the effect of different ϵ \epsilon settings. Based on the table, we can see that our low-rank isotropic Gaussian distribution consistently outperforms both FR and C-STD baselines across multiple metrics and datasets. For accuracy (ACC), TFB achieves the highest scores on several datasets, notably reaching 86.97 on ARC-E and 82.87 on OBQA. In terms of calibration, our approach demonstrates superior performance with significantly lower ECE scores across most IND datasets (e.g., 4.15 on WG-S, 4.77 on ARC-C, and 2.57 on ARC-E), often reducing ECE by more than 50% compared to baselines. The method also achieves optimal NLL scores on multiple datasets, including WG-S (0.61) and BoolQ (0.30). These comprehensive results clearly demonstrate that our low-rank isotropic Gaussian distribution not only improves model accuracy but also enhances calibration performance compared to alternative approaches like FR and C-STD.


## C.3 TFB Beyond the Llama2-7B Backbone

We report the detailed performance of TFB applied to various LLM backbones in Table 10 . While the baseline MLE is typically trained for 2 epochs (shown with each backbone name), we also report results with reduced training (1 epoch) for comparison. Although training with fewer steps (early stopping) can effectively reduce model overconfidence, it typically leads to performance degradation.

The results demonstrate that TFB consistently improves model calibration across different backbones while maintaining competitive accuracy. Specifically, for Llama2-7B, TFB reduces the ECE from 4.50 to 1.24 on the combined dataset while preserving the accuracy (81.32 vs 81.41). Similar improvements are observed with Llama3-8B, Llama3.1-8B, and Mistral-7B-v0.3, where TFB achieves better calibration than both the full training and early stopping baselines without sacrificing performance, suggesting its effectiveness as a general approach for enhancing LLM calibration.


## C.4 TFB Beyond the Naive LoRA

We report the detailed performance of TFB applied to various LoRA variants in Table 11 . The baseline models are trained for 2 epochs using pre-trained Llama3.1-8B on the concatenated dataset of six commonsense reasoning tasks. Specifically, we consider the two LoRA variants:

VeRA ( Kopiczko et al. 2023 ) : Uses shared low-rank matrices 𝑩 {\bm{B}} and 𝑨 {\bm{A}} across layers, with layer-specific trainable scalar vector 𝒅 {\bm{d}} and bias vector 𝒃 {\bm{b}} . Concretely, the parameterization of VeRA’s updated weight matrix 𝑾 {\bm{W}} is modeled as:

Hence after the fine-tuning of VeRA, we can easily regroup the weight matrices into { 𝑩 ′ = [ diag ⁡ ( 𝒃 ) ] ​ 𝑩 ​ [ diag ⁡ ( 𝒅 ) ] , 𝑨 ′ = 𝑨 } \{{\bm{B}}^{\prime}=[\operatorname{diag}({\bm{b}})]{\bm{B}}[\operatorname{diag}({\bm{d}})],{\bm{A}}^{\prime}={\bm{A}}\} , and apply the TFB Bayesianization scheme illustrated in Algorithm 1 .

PiSSA ( Meng et al. 2024 ) : Employs an alternative initialization scheme while maintaining LoRA’s parameterization and training procedure. Hence the TFB process for PiSSA is trivial.

The results in Table 11 show that TFB consistently improves calibration across different LoRA variants while preserving model performance. Notably, when applied to the standard LoRA, TFB significantly reduces the ECE from 4.74 to 1.05 on the combined dataset with minimal impact on accuracy (86.45 vs 86.70). Similar improvements are observed with VeRA and PiSSA variants, where TFB achieves better calibration (reducing ECE to 1.44 and 1.17 respectively) while maintaining comparable accuracy levels. These results demonstrate that TFB can effectively enhance model calibration across different LoRA architectures without compromising their performance.


## C.5 Improving the Efficiency of TFB

We report the detailed performance of last-layer TFB ( LL TFB ) in Table 12 . As indicated in the table, with only N = 10 N=10 samples, last-layer Bayesianization provides less effective uncertainty estimation compared to full-model Bayesianization. However, increasing the number of samples to N = 100 N=100 significantly enhances the posterior estimation, allowing last-layer Bayesianization to achieve better accuracy. This improvement further allows it to outperform full-model Bayesianization in terms of NLL across most datasets.