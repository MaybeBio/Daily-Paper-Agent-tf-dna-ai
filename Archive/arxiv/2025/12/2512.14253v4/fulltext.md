## FLAME: Flow Enhanced Legendre Memory Models for General Time Series Forecasting

In this work, we introduce FLAME , a family of extremely lightweight and capable Time Series Foundation Models, which support both deterministic and probabilistic forecasting via generative probabilistic modeling, thus ensuring both efficiency and robustness. FLAME utilizes the Legendre Memory for strong generalization capabilities. Through adapting variants of Legendre Memory, i.e., translated Legendre (LegT) and scaled Legendre (LegS), in the Encoding and Decoding phases, FLAME can effectively capture the inherent inductive bias within data and make efficient long-range inferences. To enhance the accuracy of probabilistic forecasting while keeping efficient, FLAME adopts a Normalization Flow based forecasting head, which can model the arbitrarily intricate distributions over the forecasting horizon in a generative manner. Comprehensive experiments on well-recognized benchmarks, including TSFM-Bench and ProbTS, demonstrate the consistent state-of-the-art zero-shot performance of FLAME on both deterministic and probabilistic forecasting tasks.


## 1 Introduction

Time Series Forecasting is a critical and widely studied task due to the attractive charm of peeking future, which helps make significant values in various fields through planning ahead. While, time series dances like a flame – it is hard to accurately capture the determinstic rules. Therefore, to control risks and make reasonable decisions, quantifying uncertainties through Probabilistic Time Series Forecasting (PTSF) is a more reliable approach, which is continously explored for decades from statistical approaches ( Godahewa et al. 2021a ; Box & Pierce 1970 ) with solid theories and interpretability to data-driven approaches ( Nie et al. 2023 ; Qiu et al. 2025e ; Wu et al. 2025b ) with strong fitting capability. Among them, deep learning models ( Nie et al. 2023 ; Qiu et al. 2025e ; Wu et al. 2025b ) show outstanding impressive performance on in-distribution tasks through effectively capturing the inherent dynamics within raw data. Inspired by the success of pretrained models in other domains such as CV ( Khan et al. 2022 ; Liu et al. 2021 ) and NLP ( Liu et al. 2024a ; Achiam et al. 2023 ) with strong generalization capabilities, a surge of pretrained time series foudation models ( Liu et al. 2024c ; Das et al. 2024 ; Gao et al. 2024 ; Shi et al. 2024 ; Wang et al. 2025b ; Wang et al. 2025c ) are developed for out-of-distribution tasks, demonstrating promising trends.

Recent studies on time series foundation models ( Woo et al. 2024 ; Shi et al. 2024 ; Wang et al. 2025b ; Liu et al. 2025d ) have achieved some progress in exploiting the generalization capabilities and exhibit excellent forecasting performance in zero-shot scenarios. Their generalization capabilities mainly come from two perspectives–see Figure 1 : 1) some works make efforts in devising appropriate Transformer-based architectures, and expanding the parameters to Hundreds-Million- or Billion-Scale ( Shi et al. 2024 ; Ansari et al. ; Woo et al. 2024 ; Das et al. 2024 ) , or with the help of the massive parameters from LLMs ( Zhou et al. 2023 ; Jin et al. 2024 ) and ViTs ( Chen et al. 2024a ) . Though these works achieve excellent performance in zero-shot scenarios, they consume a lot in inference under limited resources, and some of them are even slower than training end-to-end supervised models from scratch, thus hindering the efficiency and practicality ; 2) another branch of works explore the effective capture of inductive bias within data, with merticulously-designed lightweight structures ( Ekambaram et al. 2024 ; Gao et al. 2024 ; Wang et al. 2025b ) but strong generalization capabilites. However, although they demonstrate strong performance in determinstic forecasting tasks, they lack the support of probabilistic forecasting . Moreover, predicting accurate distributions over the forecasting horizon is difficult because assuming prior distributions like Isotropic Gaussian Distributions constrains the modeling capabilites of real data distributions. On the other hand, modeling arbitrary complex distributions relies on generative mechanisms ( Li et al. 2017 ; Kollovieh et al. 2023 ) , which may increase the model complexity and hinder the efficiency.

As shown in Figure 1 , our proposed FLAME pionners the exploration of lightweight time series foundation models capable of both determinstic and probabilistic forecasting . To enhance the generalization capability while keeping lightweight, we utilize the Legendre Memory ( Voelker et al. 2019 ; Gu et al. 2020 ) in both Encoding and Decoding phases to capture the inherent inductive bias within data, which contributes to a lightweight but strong framework. Originating from ordinary differential equations (ODEs) and characterized by orthogonal legendre polynomials, the Legendre Memory has been utilized in control theory to model continuous time-delay systems ( Richard 2003 ) for several decades, which has the potential to compress time series of varying lengths into vectors of the same size. This helps ensuring lightweight, and we employ Legendre Memory in both the encoder and decoder.

First, in the pretraining process of time series foundation models, the inherent periods and trends of data from distinct domains can lead to complex local characteristics but the patching technique cannot handle this due to the fixed receptive field. This inspires us to devise a Local-Perception module to unlock the power of Legendre Memory in integrating intricate and varying local characteristics within data as the supplement environmental semantic information to patched tokens. Second, we also adopt the Structured State-Space Duality (SSD ( Dao & Gu 2024 ) ) layers in the decoding phase, which utilizes the Legendre Memory to initialize the state transition matrices ( Gu et al. 2020 ) , exceling at modeling long time series based on its selective states and adaptive memory utilization.

Besides the adaptions of Legendre Memory, we also devise a Flow-based Head to support generative probabilistic forecasting. Specifically, we focus on token-wise modeling, which constructs the distributions over dozens of time series points at once, and using the Flow-based Head driven by normalization flow ( Rasul et al. 2021b ; Durkan et al. 2019 ) can preserve both considerable efficiency and interpretability compared with prevailing diffusion models ( Kollovieh et al. 2023 ; Rasul et al. 2021a ) . Additionally, we also devise to capture the token-wise causality in the Flow-based Head, which is important but neglected in current decoding methods ( Liu et al. 2025d ; Liu et al. 2024c ; Shi et al. 2024 ) , and this can help preserve temporal dependencies within tokens to boost the fine-grained modeling. Through these adaptions, the Flow-based Head can preserve both the accuracy and efficiency through constructing lightweight couple layers to simulate the reversible conditional transfer process from fixed prior Gaussian distributions to any complex real-data distribution. With the Legendre Memory and Flow-based Head facilliating the strong generative paradigm, FLAME can make extreme fast and accurate probabilistic forecasts. Our contributions are summarized as:

We present FLAME , a family of Fl ow enh a nced Legendre Me mory Foundation Models, including three parameter versions, i.e., 2M, 6M, 10M. Even the largest version of FLAME (10M) is far more lightweight than other time series foundation models which supports both determinstic and probabilistic forecasting.

We adapt the Legendre Memory to enhance the generalization capability. Both the Local-Perception Module and SSD-Decoder are driven by Legendre Memory and able to adaptively utilize the inductive bias within data.

We devise the Flow-based Head to model the intricate token-wise distributions over the forecasting horizon, considering the causality within tokens, with strong efficiency and accuracy.

Experimentally, FLAME achieves state-of-the-art zero-shot performance on both determinstic and probabilistic forecasting benchmarks, including TSFM-Bench ( Li et al. 2025c ) and ProbTS ( Zhang et al. 2024 ) , demonstrating a strong out-of-the-box tool of decision intelligence. The resources are available at https://anonymous.4open.science/r/FLAME-D83F .


## 2 Legendre Memory

When modeling sequence data with recurrent networks, “memory” is a common concept denoting the online compression capability of historical observations. Among them, Legendre Memory ( Voelker et al. 2019 ; Gu et al. 2020 ) is a kind of continuous online function approximation, which utilizes orthogonal Legendre polynomials to compress the continous-time history f f into state vectors m m with fixed sizes. From the perspective of Real Analysis , given a time-varying measure μ ( t ) \mu^{(t)} and a high-order polynomial operator , recent history f f can be compressed into state vectors m m under certain approximation error ( Gu et al. 2020 ) . When the operator is the Legendre polynomial, there exists two common time-varying measures: translated Legendre (LegT) and scaled Legendre measure (LegS) .

LegT assigns uniform weights to the most recent history [ t − θ , t ] [t-\theta,t] , where θ \theta denotes the length of the sliding windows, or the length of history that is being summarized:

Under the LegT measure, the process of compressing the historical information f f into state vectors m m can be represented as solving d d coupled linear time-invariant ODEs:

where A ∈ ℝ d × d , B ∈ ℝ d × 1 A\in\mathbb{R}^{d\times d},B\in\mathbb{R}^{d\times 1} are optimal parameters derived through the use of Padé approximant ( Padé 1892 ; Voelker 2019 ) . In the forward process, the sequence of [ t − θ , t ] [t-\theta,t] can be compressed into the memory cell m ⁡ ( t ) ∈ ℝ d m(t)\in\mathbb{R}^{d} in a recurrent mode using discretized Formula ( 2 ):

where A ¯ \bar{A} and B ¯ \bar{B} can be obtained through zero-order hold (ZOH). And the “memory” lies in the capability of using m ⁡ ( t ) m(t) to recover all the past history f f of [ t − θ , t ] [t-\theta,t] , thus can describe a θ \theta time-delay system ( Richard 2003 ) :

where 𝒫 i ​ ( r ) \mathcal{P}_{i}(r) is the i i -th shifted Legendre polynomial ( Voelker et al. 2019 ) . According to Theorem 2.1 ( Gu et al. 2020 ) , larger number d d of Legendre Polynomials basis leads to more accurate approximation.

If F ⁡ ( x ) F(x) is L L -Lipschitz, then ‖ F [ t − θ , t ] ​ ( x ) − f [ t − θ , t ] ​ ( x ) ‖ μ ( t ) ≤ 𝒪 ⁡ ( θ ​ L / d ) \|F_{[t-\theta,t]}(x)-f_{[t-\theta,t]}(x)\|_{\mu^{(t)}}\leq\mathcal{O}(\theta L/\sqrt{d}) . Moreover, if F ⁡ ( x ) F(x) has k k -th order bounded derivatives, we have ‖ F [ t − θ , t ] ​ ( x ) − f [ t − θ , t ] ​ ( x ) ‖ μ ( t ) ≤ 𝒪 ⁡ ( θ k ​ d − k + 1 / 2 ) \|F_{[t-\theta,t]}(x)-f_{[t-\theta,t]}(x)\|_{\mu^{(t)}}\leq\mathcal{O}(\theta^{k}d^{-k+1/2}) .

Compared with LegT, LegS assigns uniform weights to all history [ 0 , t ] [0,t] to support the compression of the entire history:

Under the LegS measure, the compressing process is:

where A ∈ ℝ d × d A\in\mathbb{R}^{d\times d} and B ∈ ℝ d × 1 B\in\mathbb{R}^{d\times 1} can also be discretized as Formula ( 5 ) and Formula ( 6 ).


## 3 FLAME

FLAME adopts the Channel-Independent ( Nie et al. 2023 ) pretraining paradigm, and each variable is preprocessed through Instance Normalization ( Ulyanov et al. 2016 ) to mitigate the value discrepancy. As shown in Figure 2 , FLAME utilizes the Re-Norm ( Kim et al. 2021 ) to further mitigate the statistical differences between inputs and forecasts, and its backbone mainly consists of three modules: 1) Encoding, including Time Series Tokenization, Local-Perception, and MSA-Encoder, which tokenize the time series and enhance them through fusing the local environmental information with LegT; 2) Decoding, including LegS based SSD-Decoder and MCA-Enhancer, which utilize the SSD layers and MCA layers to make long-term inference; 3) Flow-based Head, which leverages the Normalization Flow to support generative probabilistic forecasting.


## 3.1 Encoding

In the pretraining Time Series Corpus, all data are preprocessed into univariate time series and received by FLAME in a Channel-Independent paradigm. Following the commonly used patching technique, which is first introduced by Triformer ( Cirstea et al. 2022 ) , we first divide each univariate time series X ∈ ℝ T X\in\mathbb{R}^{T} into non-overlapping time series patches:

where X P ∈ ℝ n × p X^{P}\in\mathbb{R}^{n\times p} are the patches, n = ⌈ T / p ⌉ n=\lceil T/p\rceil denotes the patch numer and p p is the patch size. h i ∈ ℝ p h_{i}\in\mathbb{R}^{p} is the i i -th patch. Subsequently, we use a linear layer: ℝ p → ℝ d \mathbb{R}^{p}\to\mathbb{R}^{d} to transform the patches to tokens:

where X t ​ o ​ k ​ e ​ n ∈ ℝ n × d X^{token}\in\mathbb{R}^{n\times d} are the embeded time series tokens. Patch-wise tokens preserve semantic information and reduce the number compared with point-based tokens, thus enhancing efficiency.

Though patching technique ( Cirstea et al. 2022 ; Nie et al. 2023 ) has achieved some progress in time series foundation models, its fixed receptive field may limit models’ generalization capabilities, thus requiring heavy backbones. The core reason is that the inherent periods and trends within data vary across datasets from distinct domains, causing the diversity of frequencies, but the fixed patch size in pretrained models only captures the same span without considering the changing surrounding environmental information.

Specifically, in pretraining scenarios, a patch with the fixed length may cover the whole period in one pretraining dataset and only covers, e.g., the 70% period in another–see Figure 2 (b), which causes burden to understand this semantic transformation. To tackle this limitation, we manage to recognize the varying periods, then align their information with patch-wise tokens to supplement the environmental semantics. First, we adopt the FFT ( Brigham & Morrow 1967 ) to find the period of the input series:

where FFT ​ ( ⋅ ) \text{FFT}(\cdot) and Amp ​ ( ⋅ ) \text{Amp}(\cdot) denote the FFT and the calculation of amplitude values. P \mathrm{P} is the searched period length. Then we consider the relative positional relations between the patch and the surronding period to make alignment:

where X P ′ ∈ ℝ n × ( p + s ) X^{P^{\prime}}\in\mathbb{R}^{n\times(p+s)} are the local environmental patches. The padding length s s is used to make each local environmental patch w i ∈ ℝ p + s w_{i}\in\mathbb{R}^{p+s} cover the corresponding patch h i ∈ ℝ p h_{i}\in\mathbb{R}^{p} , and p + s p+s is the integer multiple of the period P \mathrm{P} . These operations can help align the intricate and varying local information w i w_{i} to the patch h i h_{i} .

For each w i ∈ ℝ p + s w_{i}\in\mathbb{R}^{p+s} , its length varies with the sample during pretraining due to the multiple frequencies of the time series corpus, which is hard to be encoded through predefined neural networks like MLPs. To overcome this, we propose to utilize the LegT Legendre Memory–see Section 2 , to encode the varying local environmental information, i.e., the varying periods, into vectors of the fixed size. For each w i ∈ ℝ p + s w_{i}\in\mathbb{R}^{p+s} , we use the discretized form of LegT to compress it like a state space model in an autoregressive manner:

where θ = p + s \theta=p+s is determined based on the length of w i w_{i} , A ∈ ℝ d × d A\in\mathbb{R}^{d\times d} and B ∈ ℝ d × 1 B\in\mathbb{R}^{d\times 1} are untrainable and initialized through Formula ( 4 ), Δ ​ t \Delta t is a predefined parameter to control the granularity of zero-order hold (ZOH). This mechanism compresses the local environmental patch w i ∈ ℝ p + s w_{i}\in\mathbb{R}^{p+s} with varying lengths into the memory cell m t ∈ ℝ d m_{t}\in\mathbb{R}^{d} with the fixed size . The generated environmental tokens are:

where each token w i ′ ∈ ℝ d w^{\prime}_{i}\in\mathbb{R}^{d} is the last state of memory cell. We then fuse the original tokens X t ​ o ​ k ​ e ​ n X^{token} and the environmental tokens X t ​ o ​ k ​ e ​ n ′ X^{token^{\prime}} into H ∈ ℝ n × d H\in\mathbb{R}^{n\times d} : H = X t ​ o ​ k ​ e ​ n + X t ​ o ​ k ​ e ​ n ′ H=X^{token}+X^{token^{\prime}} . According to Theorem 2.1 , the dimension d d is often greater than θ \theta , which helps preserve the full semantics.

After obtaining the fused tokens, we use the Multi-head Self-Attention Layer as the encoder to generate the hidden representations of them. Through fully-connected interaction, the MSA-Encoder aims at learning the similarities and differences among patterns and environmental information within the tokens:

the representations H ′ ∈ ℝ n × d H^{\prime}\in\mathbb{R}^{n\times d} are the outputs of the Encoding phase, and provide rich semantics within data.


## 3.2 Decoding

We utilize LegT in Local-Perception of the Encoding phase to enrich the local environmental information. In the Decoding phase, the long-range modeling capability gains more attention, which calls for adaptive memory utilization when making long-term forecasts. Structured State-Space Duality (SSD) Layer or Mamba2 ( Dao & Gu 2024 ) , uses the selective state space modeling mechanism to adaptively process historical information, significantly improving efficiency while achieving similar accuracy to Transformers. Its mechanism takes the form as follows:

where the form shares similarities with LegS, see–Formula ( 10 ). Previous works ( Gu & Dao 2023 ; Dao & Gu 2024 ) demonstrate that adapting A , B , C A,B,C to selective A t , B t , C t A_{t},B_{t},C_{t} can enhance the non-linearity capability. Among them, A t A_{t} is obtained from A A through the learnable granularity Δ ​ t \Delta t of discretization, so that the initialization of A A still matters. To preserve the capability of adaptive memory utilization and ensure the linear complexity of SSD, we use the diagnoal of A A in LegS–see Formula ( 12 ), as the initialization of A t A_{t} . We then use the SSD layer with initialized A t A_{t} as the Decoder to forecast the future tokens:

where F ∈ ℝ l × d F\in\mathbb{R}^{l\times d} . Supposing the length of forecasting horizon is L L , l = ⌈ L / p ⌉ l=\lceil L/p\rceil . Based on the LegS, SSD-Decoder can efficiently memorize all the information from inputs and adaptively utilize them like Transformers.

We then use the Multi-head Cross-Attention Layer to further enhance the outputs through recalling the similar representations in the inputs. Specifically, we set F F as Query, H ′ H^{\prime} as Key and Value. Through skip connections in MCA-Enhancer, it effectively enhances the F F :

where F ′ ∈ ℝ l × d F^{\prime}\in\mathbb{R}^{l\times d} are the outputs of the Decoding phase, which contain the high-order semantic information obtained from the token transition process in the hidden spaces.


## 3.3 Flow-based Head

Through pretraining on Time Series Corpus from multiple domains, the Encoding and Decoding phases of FLAME possess strong capability of modeling the token transition principles, which means F ′ ∈ ℝ l × d F^{\prime}\in\mathbb{R}^{l\times d} are high-quality representations for forecasting. In time series foundation models, making token-wise forecasts through relative lightweight heads can preserve efficiency and ensure the heavy backbones do learn the “knowledge” ( Liu et al. 2024c ; Liu et al. 2025d ) .

However, since the inherent temporal causality within time series data, patch-based forecasting models only model the token-wise causal relationships in decoding. When transforming these high-dimension tokens into patch sizes for forecasts, the fine-grained causal relationships within each patch are often neglected. To support generative probabilistic forecasting, keep lightweight, and capture such fine-grained causal relationships, we merticulously devise the couple layers of Normalization Flow to model the intricate probabilistic distributions of real-data. The whole generative process is fourmulated as:

where we utilize the tokens F ′ = [ o 1 , o 2 , ⋯ , o l ] ∈ ℝ l × d F^{\prime}=[o_{1},o_{2},\cdots,o_{l}]\in\mathbb{R}^{l\times d} as the prior conditions, and the Gaussian Noise ϵ i ∈ ℝ p \epsilon_{i}\in\mathbb{R}^{p} is the initialization. We concat them to obtain ℱ i ∈ ℝ p + d \mathcal{F}_{i}\in\mathbb{R}^{p+d} as the input of couple layers. The structure of couple layers f i f_{i} is the masked MLP:

where the mask ℳ ∈ ℝ ( p + d ) × ( p + d ) \mathcal{M}\in\mathbb{R}^{(p+d)\times(p+d)} determines the connection pattern of neurons in MLP-based couple layer f i := MLP ℳ i f_{i}:=\text{MLP}^{i}_{\mathcal{M}} , which determines the interactions among dimensions of ℱ i ∈ ℝ p + d \mathcal{F}_{i}\in\mathbb{R}^{p+d} . Considering the output ℱ i ′ ∈ ℝ p + d \mathcal{F}^{\prime}_{i}\in\mathbb{R}^{p+d} , ℳ n , k = 0 \mathcal{M}_{n,k}=0 indicates that ℱ i ′ ​ [ k ] \mathcal{F}^{\prime}_{i}[k] cannot see ℱ i ​ [ n ] \mathcal{F}_{i}[n] when calculated in f i f_{i} , and vice versa. This means f i f_{i} allows the conditional part o i ∈ ℝ d o_{i}\in\mathbb{R}^{d} of ℱ i \mathcal{F}_{i} to self-interact and interact with all the dimension of ϵ i ∈ ℝ d \epsilon_{i}\in\mathbb{R}^{d} , and works in an autoregressive manner to ensure the noise part ϵ i ​ [ j ] \epsilon_{i}[j] only interacts with ϵ i [ ≤ j ] \epsilon_{i}[\leq j] to preserve the fine-grained causal relationships within each patch–see Figure 2 (f). Through K K coupled layers of generative probabilistic modeling, the final outputs are:

where Y ^ ∈ ℝ l × p \hat{Y}\in\mathbb{R}^{l\times p} can be further flattened and fetched the first L L points as the forecasts. With the MLP-based couple layers, Flow-based Head can achieve intricate distributional transformation while keeping lightweight. Due to the probabilistic generative mechanism, multiple samplings are recommended to evaluate the forecasted distributions. For clarity, we replace Y ^ i \hat{Y}_{i} and ℱ i \mathcal{F}_{i} with x x and z z in the token-wise optimization objective:


## 4 Experiments

We introduce the detailed experimental settings in Appendix A , and show the zero-shot performance of FLAME in Section 4.1 (deterministic) and Section 4.2 (probabilistic). We also make detailed analysis on key components of FLAME to reveal where the generalization capability comes in Section 4.3 . To analyze the scability of FLAME, we make studies on training and inference in Section 4.4 . As an important property for deployment, we also analyze the efficiency of FLAME in Section 4.5 . In summary–see Figure 3 , our proposed FLAME achieves most 1st counts and keeps the most lightweight. We provide all results in Appendix C , including full results of Table 1 and 2 , and other results on full-shot settings and short-term forecasting.


## 4.1 Deterministic Forecasting

As shown in Table 1 , the FLAME family consistently outperforms other advanced time series foundation models on datasets from TSFM-Bench. Compared with the recent state-of-the-art models Sundial, FLAME Large outperforms it in most settings, achieving most 1st counts in zero-shot deterministic forecasting tasks. Note that even the FLAME Small (2M) can achieve competitive performance with Sundial Base (128M) while only possessing the 1/64 parameter scale. Compared with the heaviest model Time-MoE Ultra (2.4B), FLAME Small possesses the 1/1,200 parameter scale but achieves average MSE reduction of 15.0% . Considering lightweight baselines like UniTS and ROSE, FLAME Small also shows excellent advantages in generalization capabilities, achieving significant average MSE reductions of 26.3% and 17.4% .


## 4.2 Probabilistic Forecasting

Table 2 represents the results of probabilistic forecasting on ProbTS. Among time series foundation models, only FLAME and Sundial adopt generative probabilistic modeling and show excellent advantages over other models. Considering the accuracy, FLAME Large achieves the most 1st counts in zero-shot probabilistic forecasting tasks, exceling both the periodic scenarios like ETT and Weather, and unstationary scenarios like Exchange and ILI. Compared with the previous well-recognized baseline MOIRAI Large and Chronos Large, FLAME Large achieves significant average CRPS reductions of 34.3% and 18.1% , demonstrating the strong capability of modeling intricate distributions over the forecasting horizons. We observe that FLAME’s zero-shot performance can even outperform the full-shot baselines a lot. Compared with diffusion-based CSDI and Flow-based GRU NVP, which need dozens of hours to train from scratch on a large dataset, FLAME Large separately achieves average 23.5% and 35.1% CRPS reduction. This demonstrates the effectiveness of Flow-based head in FLAME, which provides both efficiency and accuracy.


## 4.3 Model Analysis

To reveal where the generalization capability of FLAME comes, we analyze the key components of FLAME including Local-Perception, SSD-Decoder, and Flow-based Head in Table 3 . Results show that all of our designs are the most reasonable, see–Appendix B for full results and analytics.


## 4.4 Scability Analysis

Though the FLAME family possesses extremely lightweight backbones while achieving state-of-the-art performance, we reveal that it also possesses the potential of scability. As shown in Figure 4 , the training curves of the FLAME family indicate that the model capacity increases with the parameter scale. According to the results in Table 1 – 2 , the zero-shot performance also gets better and the FLAME Large achieves most 1st Counts in both deterministic and probabilistic forecasting tasks.

Since FLAME models distributions over the forecasting horizon, we also study the scability of generative forecasting by exploring the correlations between the sampling number and performance–see Figure 5 . The results show that the CPRS and NMAE keep consistent promotion as the sampling number increases, and achieve good performance in the number of 100, which may not cause large efficiency burdens in real-world applications.


## 4.5 Efficiency Analysis

As a characteristic property of FLAME, the extreme efficiency owes to the lightweight backbone and Flow-based Head. For detailed quantification, we report the Parameter scale, Multiply-Accumulate Operations (MACs), Max GPU Memory Occupation, and Inference Time in Table 4 . We compare the FLAME Large with time series foundation models and end-to-end supervised probabilistic models.

Results show FLAME Large achieves consistent efficiency advantages over other time series foundation models. Compared with end-to-end supervised models like TimeGrad and CSDI, FLAME Large also has less parameters, faster inference speed, and less MACs and GPU Memory.


## 5 Related works


## 5.1 Time Series Forecasting

Deterministic Time Series Forecasting is critical in decision intelligence, which has facilitated a surge of modern deep learning methods like PatchTST ( Nie et al. 2023 ) , Pathformer ( Chen et al. 2024b ) , and DUET ( Qiu et al. 2025e ) . LMU ( Voelker et al. 2019 ) and FiLM ( Zhou et al. 2022 ) first introduce Legendre Memory (LegT) in time series forecasting but they consider compressing the whole input series into state vectors, which may cause the information loss. Compared with them, FLAME leverages the LegT in compressing varying token-wise environmental information and aligning them with the original tokens, thus adapting to the multiple frequencies in pretraining corpus and obtaining strong generalization capabilities. Another important direction is Probabilisic Time Series Forecasting, which can quantify the uncertainties and produce more practical significance in real-world applications. Recently, generative mechanims such as VAE, Diffusion, and Flow are widely studied. Among them, D 3 D^{3} VAE ( Li et al. 2022 ) and K 2 K^{2} VAE ( Wu et al. 2025b ) are the most advanced VAE models in probabilistic time series forecasting. Considering multi-step generative mechanisms like Diffusion and Normalization Flow, recent models include GRU NVP ( Rasul et al. 2021b ) , CSDI ( Tashiro et al. 2021 ) , TimeGrad ( Rasul et al. 2021a ) , and TSDiff ( Kollovieh et al. 2023 ) , showing strong performance. Compared with them, FLAME is the first foundation model to adapt normalization flow for token-wise probabilistic modeling.


## 5.2 Time Series Foundation Models

Recent studies on Time Series Foundation Models manage to reveal the source of generalization capability. Distinct Tranformer-based architectures are devised and heavily stacked, and are trained on billion- or trillion-scale time series corpus, to make efforts in capturing the inherent inductive bias within data. Among them, TimesFM ( Das et al. 2024 ) , Timer ( Liu et al. 2024c ) , and Time-MoE ( Shi et al. 2024 ) are strong deterministic forecasting baselines, with hevay backbones and strong zero-shot performance. However, works like UniTS ( Gao et al. 2024 ) , TinyTTM ( Ekambaram et al. 2024 ) , ROSE ( Wang et al. 2025c ) also demonstrate that light backbones can also achieve state-of-the-art deterministic forecasting performance if the inductive bias is captured in a more efficient way. Some time series foundation models support probabilistic forecasting, among them, Lag-Llama ( Rasul et al. 2023 ) , Chronos ( Ansari et al. ) , Moirai ( Woo et al. 2024 ) , and Sundial ( Liu et al. 2025d ) have outperformed some end-to-end supervised probabilistic models. However, all of them possess hevay backbones with hundreds-million to billion parameters, which are not very efficient in making generative probabilistic forecasts on large downstream datasets. Moreover, no existing methods explore how to achieve outstanding probabilistic forecasting performance with lightweight architectures. In this paper, we propose FLAME to handle this bottleneck.


## 6 Conclusion

In this work, we propose a family of extremely lightweight and highly capable time series foundation models, named FLAME. To sum up, FLAME adapts the Legendre Memory in the backbone to compress varying local environmental information into time series tokens and support adaptive memory utilization in long-range forecasting, thus obtaining strong generalization capabilities. FLAME also supports probabilistic time series forecasting through a Normalization Flow based forecasting head. Comprehensive experiments on deterministic and probabilistic forecasting tasks demonstrate that FLAMEs are strong out-of-the-box tools of decision intelligence, possessing both accuracy and efficiency.

In the future work, we will further explore the non-deterministic modeling in all the tasks of time series analysis, e.g., probabilistic imputation, time series generation, anomaly detection, and classification. Another direction is to develop more lightweight and robust mechanisms to support generative modeling, and extend them via pretraining to the out-of-the-box paradigm.


## References


## Appendix A Implementation Details


## A.1 Pretraining Corpus

To pre-train our model, we utilize a broad collection of time series datasets drawn from multiple sources, including selected subsets from the Monash ( Godahewa et al. 2021b ) , UEA ( Bagnall et al. 2018 ) , and UCR ( Dau et al. 2019 ) repositories, along with several widely-used benchmarks ( Zhang et al. 2017 ; Wang et al. 2024 ; Liu et al. 2022 ; McCracken & Ng 2016 ; Taieb et al. 2012 ) . A full inventory of these datasets is provided in Table 5 . We ensure that none of the pre-training datasets overlap with those used in downstream evaluations. It’s also worth noting that although both the pre-training and target sets include weather data, the former is univariate while the latter contains multivariate sequences. We categorize the pre-training datasets into six domain-specific groups: Energy, Nature, Health, Transport, and Web. These datasets vary significantly in sampling rates, ranging from milliseconds to monthly intervals, capturing the diversity and richness of real-world time series. All datasets are decomposed into univariate sequences and FLAME is trained using a Channel Independent (CI) strategy.


## A.2 Baselines

For zero-shot deterministic forecasting, we compare the FLAME family against 8 advanced foundation models: Sundial ( Liu et al. 2025d ) , ROSE ( Wang et al. 2025c ) , Timer ( Liu et al. 2024c ) , MOIRAI ( Woo et al. 2024 ) , Chronos ( Ansari et al. ) , LightGTS ( Wang et al. 2025b ) , Time-MoE ( Shi et al. 2024 ) , and TinyTTM ( Ekambaram et al. 2024 ) . For zero-shot probabilistic forecasting, we compare the FLAME family with 4 foundation models: Sundial ( Liu et al. 2025d ) , MOIRAI ( Woo et al. 2024 ) , Chronos ( Ansari et al. ) , and Lag-Llama ( Rasul et al. 2023 ) , and 4 advanced end-to-end supervised models including TSDiff ( Kollovieh et al. 2023 ) , TimeGrad ( Rasul et al. 2021a ) , CSDI ( Tashiro et al. 2021 ) , and GRU NVP ( Rasul et al. 2021b ) . The corresponding codebases and implementation details are summarized in Table 6 .


## A.3 Benchmarks

To thoroughly assess the effectiveness of FLAME, we conduct experiments on TSFM-Bench ( Li et al. 2025c ) and ProbTS ( Zhang et al. 2024 ) . Our evaluation spans 11 deterministic and 9 probabilistic forecasting datasets.

For deterministic forecasting, we use ETTm1, ETTm2, ETTh1, ETTh2, Weather, Electricity, Traffic, Solar, PEMS08, Wind, and NYSE from TSFM-Bench. For most datasets, the prediction length is set to L ∈ { 96,192,336,720 } L\in\{96,192,336,720\} , while NYSE uses L ∈ { 24 , 36 , 48 , 60 } L\in\{24,36,48,60\} .

For probabilistic forecasting, we adopt ETTm1, ETTm2, ETTh1, ETTh2, Weather, Electricity, Traffic, Exchange, and ILI from ProbTS. The prediction length is set to L ∈ { 96,192,336,720 } L\in\{96,192,336,720\} for most datasets, while ILI-L uses L ∈ { 24 , 36 , 48 , 60 } L\in\{24,36,48,60\} .

All models are configured with the contextual length of the best performance recommended in their papers. It is important to clarify that datasets shared in both the TSFM-Bench and ProbTS (e.g., ETTh1, Traffic) are different in evaluation settings like strides. A summary of dataset statistics can be found in Table 7 .


## A.4 Experimental Settings

We implement the FLAME family using Distributed Data Parallel in PyTorch ( Paszke et al. 2019 ) , and conduct all experiments on 8 NVIDIA A800 GPUs with 80GB GPU memory. The model is optimized using the AdamW optimizer with an initial learning rate of 5 × 10 − 5 5\times 10^{-5} . To progressively reduce the learning rate during training, we employ a step decay schedule via the StepLR scheduler. During pre-training, we use 12 historical tokens and 4 prediction tokens, with a reference patch size p = 48 p=48 . The batch size is set to 8,192. Full details on model configurations and parameter sizes are summarized in Table 8 .

For downstream forecasting tasks, we apply periodic patching strategies adapted to each dataset’s temporal characteristics. The number of past tokens remains fixed at 11, while the prediction lengths are evaluated at 96, 192, 336, and 720 steps.

We also address the "Drop Last" issue highlighted in recent studies ( Qiu et al. 2024 ; Qiu et al. 2025c ; Li et al. 2025c ) , where setting drop_last =True during test evaluation may lead to misleading results due to incomplete batches. To ensure consistency and fairness, we set drop_last =False for all baseline models in our experiments.


## A.5 Evaluation Metrics

Regarding evaluation metrics, following the experimental setup in TSFM-Bench, we adopt Mean Squared Error (MSE) and Mean Absolute Error (MAE) as evaluation metrics for deterministic forecasting. For probabilistic forecasting, we use Continuous Ranked Probability Score (CRPS) and Normalized Mean Absolute Error (NMAE) in ProbTS. Considering the case with K K variates and T T forecasting horizon.

The Mean Squared Error quantifies the average of the squared differences between predicted values and their corresponding ground truths. It penalizes larger errors more heavily due to the squaring operation, making it sensitive to outliers. Formally, it is defined as:

where K K denotes the number of variables, T T the prediction horizon, x t k x^{k}_{t} the true value, and x ^ t k \hat{x}^{k}_{t} the predicted value.

The Mean Absolute Error calculates the average magnitude of prediction errors without considering their direction. By focusing on the absolute differences, MAE provides a robust and interpretable measure of accuracy:

where all terms follow the same definition as above. Unlike MSE, MAE treats all errors equally and is less sensitive to large deviations.

The CRPS assesses the quality of probabilistic forecasts by comparing the predicted cumulative distribution function (CDF) F F with the observed outcome x x . It is computed as:

where 𝕀 { x ≤ z } \mathds{I}\{x\leq z\} is the indicator function. CRPS rewards distributions that assign high probability to the true value and achieves its minimum when the predicted distribution matches the true distribution. In practice, we approximate CRPS using the empirical CDF F ^ ( z ) = 1 n ∑ i = 1 n 𝕀 { X i ≤ z } \hat{F}(z)=\frac{1}{n}\sum_{i=1}^{n}\mathds{I}\{X_{i}\leq z\} based on n = 100 n=100 samples drawn from the conditional predictive distribution p θ ​ ( 𝒙 t | 𝒉 t ) p_{\theta}(\bm{x}_{t}|\bm{h}_{t}) .

The NMAE extends MAE by normalizing it against the total magnitude of ground-truth values, thereby enabling fair comparison across datasets with varying scales. Its formula is:


## Appendix B Full Model Analytics


## B.1 Analytics of Sampling Number

Given that FLAME models distributions across the forecasting horizon, we conduct an in-depth study on the scalability of generative forecasting by examining the correlations between the sampling number and performance, as presented in Table 9 . Specifically, we choose four sampling numbers: 10, 20, 50, and 100. The findings indicate that both CPRS and NMAE demonstrate a consistent improvement as the sampling number rises. Moreover, a sampling number of 100 leads to excellent performance, and this is unlikely to impose significant efficiency burdens in practical applications.


## B.2 Analytics of Local-Perception

As shown in Table 10 , we select three variants to assess the Local-Perception. These variants include eliminating the entire Local-Perception (termed as “w/o Local-Perception”), encoding the closest single period without performing alignment (referred to as “w/o Period Alignment”), and making the initialized matrices A , B A,B learnable (denoted as “Learnable LegT”). Our observations indicate that Local-Perception indeed has a significant impact. Specifically, the variant lacking Local-Perception experiences a collapse in zero-shot performance. Period Alignment is also of importance. When considering datasets such as Electricity and Traffic, which contain complex periodic information, the zero-shot performance deteriorates substantially without the assistance of Period Alignment. Regarding Learnable LegT, its performance shows a slight decline when the initialized matrices A , B A,B are made learnable. This is because, upon being pretrained on a large-scale time series corpus, the Legendre coefficients within the matrices may gradually change, thereby losing the on-line approximation capability.


## B.3 Analytics of SSD-Decoder

Subsequently, we conduct a comparison between the SSD-Decoder and the decoders of other mechanisms in Table 11 . More precisely, we select the Self-Attention Decoder, Causal-Attention Decoder, and Mamba v1 Decoder as the baselines. In the context of forecasting tasks, causal correlations are more suitable. As a result, the Self-Attention Decoder exhibits the poorest performance. We further note that the SSD-Decoder outperforms both the Mamba v1 Decoder and the Causal-Attention Decoder, which showcases its superior ability to leverage memory during the forecasting process.


## B.4 Analytics of Flow-based Head

To assess the efficacy of the Flow-based Head, we choose alternative generative mechanisms to implement forecasting heads as baselines–see Table 12 . These include Variational AutoEncoder (VAE), Diffusion, and Flow Match. Given that the VAE adheres to a one-step generation paradigm, it exhibits subpar performance in scenarios such as Electricity and Traffic. This is because accurately generating distributions over the complex real-world forecasting horizon in these scenarios poses a significant challenge. Regarding Diffusion and Flow Match, although they possess robust multi-step generation paradigms, our findings indicate that they are not as potent as our meticulously-designed Flow-based Head.


## Appendix C Full Results


## C.1 Full zero-shot results

We provide all the results of the zero-shot deterministic forecasting in Table 13 . As shown in Table 13 , we include 11 representative real-world datasets from TSFM-Bench, demonstrating that FLAME achieves state-of-the-art forecasting performance.

We provide all the results of the zero-shot probabilistic forecasting in Table 14 . As shown in Table 14 , we include 9 representative real-world datasets from ProbTS, demonstrating that FLAME achieves state-of-the-art forecasting performance.

Considering short-term forecasting, we also conduct experiments on 8,068 univariate datasets in TFB ( Qiu et al. 2024 ) , we report the average MASE and msMAPE results in Figures 6 and 7 . FLAME Large outperforms all baselines including end-to-end supervised models and foundation models.


## C.2 Full-shot and few-shot results

We further compare FLAME Small with end-to-end supervised models. We provide all the results of deterministic forecasting in Table 15 , comparing FLAME Small of different training budgets with most advanced end-to-end determinsitic forecasting models.

We also provide all the results of probabilistic forecasting in Table 16 , comparing FLAME Small of different training budgets with most advanced end-to-end probabilistic forecasting models.


## Appendix D Showcases

We visualized the forecasting results of FLAME Large on TSFM-Bench and TFB in Figures 8 and 9 .


## Appendix E Related Works

Time Series Analysis holds a position of paramount importance across a diverse range of fields, including the economy ( Qiu et al. 2025b ; Qiu et al. 2025a ; Liu et al. 2025a ) , transportation ( Wu et al. 2025d ; Wu et al. 2024 ) , health ( Lu et al. 2023 ; Lu et al. 2024a ; Lu et al. 2024b ) , weather ( Li et al. 2025a ; Yang et al. 2024 ; Zhou et al. 2025 ) , and energy ( Sun et al. 2025a ) . It encompasses a multitude of critical tasks, such as forecasting ( Li et al. 2025b ; Dai et al. 2024c ) , anomaly detection ( Wang et al. 2025a ; Qiu et al. 2025c ; Wu et al. 2025c ; Zhang et al. 2025 ) , classification ( Liu et al. 2024b ) , imputation ( Wu et al. 2023 ) , and others ( Qiu et al. 2025f ; Wu et al. 2025b ) . Among these tasks, Time Series Forecasting is the one most extensively applied in practical, real-world scenarios.

Time series forecasting (TSF) involves the prediction of future observations on the basis of historical data. Research results have demonstrated that features learned through specific methods may present superior performance in comparison to human-designed features ( Dai et al. 2024b ; Hu et al. 2025a ; Dai et al. 2024c ; Liu et al. 2025c ; Sun et al. 2025b ; Sun et al. 2025a ; Niu et al. 2025 ; Qiu et al. 2025d ) . By leveraging the representation learning capabilities of deep neural networks (DNNs), numerous deep-learning based approaches have come into existence. For example, TimesNet ( Wu et al. 2023 ) and SegRNN ( Lin et al. 2023 ) model time series as vector sequences, utilizing CNNs or RNNs to capture temporal dependencies. Furthermore, Transformer architectures, including Informer ( Zhou et al. 2021 ) , Dsformer ( Yu et al. 2023 ) , TimeFilter ( Hu et al. 2025b ) , TimeBridge ( Liu et al. 2025b ) , PDF ( Dai et al. 2024a ) , Triformer ( Cirstea et al. 2022 ) , PatchTST ( Nie et al. 2023 ) , ROSE ( Wang et al. 2025c ) , LightGTS ( Wang et al. 2025b ) , and MagicScaler ( Pan et al. 2023 ) , are able to more precisely capture the complex relationships between time points, thus significantly improving forecasting performance. MLP-based methods, such as DUET ( Qiu et al. 2025e ) , SRSNet ( Wu et al. 2025a ) , APN ( Liu et al. 2026 ) , AMD ( Hu et al. 2025a ) , NLinear ( Zeng et al. 2023 ) , and DLinear ( Zeng et al. 2023 ) , adopt relatively simpler architectures with fewer parameters yet still succeed in achieving highly competitive forecasting accuracy.