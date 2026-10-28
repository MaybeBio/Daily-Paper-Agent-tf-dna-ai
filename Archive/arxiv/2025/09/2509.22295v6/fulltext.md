## Aurora: towArds Universal geneRative multimOdal time seRies forecAsting

Cross-domain generalization is very important in Time Series Forecasting because similar historical information may lead to distinct future trends due to the domain-specific characteristics. Recent works focus on building unimodal time series foundation models and end-to-end multimodal supervised models. Since domain-specific knowledge is often contained in modalities like texts, the former lacks the explicit utilization of them, thus hindering the performance. The latter is tailored for end-to-end scenarios and does not support zero-shot inference for cross-domain scenarios. In this work, we introduce Aurora, a Multimodal Time Series Foundation Model, which supports multimodal inputs and zero-shot inference. Pretrained on Corss-domain Multimodal Time Series Corpus, Aurora can adaptively extract and focus on key domain knowledge contained in corrsponding text or image modalities, thus possessing strong Cross-domain generalization capability. Through tokenization, encoding, and distillation, Aurora can extract multimodal domain knowledge as guidance and then utilizes a Modality-Guided Multi-head Self-Attention to inject them into the modeling of temporal representations. In the decoding phase, the multimodal representations are used to generate the conditions and prototypes of future tokens, contributing to a novel Prototype-Guided Flow Matching for generative probabilistic forecasting. Comprehensive experiments on well-recognized benchmarks, including TimeMMD, TSFM-Bench and ProbTS, demonstrate the consistent state-of-the-art performance of Aurora on both unimodal and multimodal scenarios.

Resources: https://anonymous.4open.science/r/Aurora-40AB .


## 1 Introduction

Time series forecasting has gained sustained attention for decades of years due to its significant values in multiple domains, including economy, transportation, meteorology, and public health. In recent years, the key pivot comes with the surge of deep learning, which brings the boom of merticulously-designed deep forecasting models ( Cirstea et al. 2022 ; Nie et al. 2023 ; Qiu et al. 2025d ; Wu et al. 2025a ) . Through learning the inherent dynamics within the raw data, deep learning models can outperform classic statistical methods ( Box & Pierce 1970 ; Mei et al. 2014 ) and obey the scaling law ( Shi et al. 2024a ; Yao et al. ) . Due to the success, it also brings the most commonly-used forecasting paradigm, which utilizes the past information to infer how the series goes in the coming horizon. Although this paradigm contributes to impressive performance under the domain-specific scenarios, its effectiveness is suspicious when facing cross-domain inference, where similar historical information may lead to different futures due to domain differences.

As shown in Figure 1 , current research of time series forecasting explores the cross-domain adaption problem in two main perspectives: 1) pre-training on cross-domain time series corpus for unimodal time series foundation models, which partially possess cross-domain generalization capablities; 2) utilizing cross-modality information in training end-to-end multimodal supervised models, which effectively integrates domain knowledge in forecasting. For time series foundation models, the cross-domain generalization capabilities mainly come from the sensitivity to subtle differences in historical information from different domains. Some of them ( Shi et al. 2024b ; Liu et al. 2025d ) are pretrained on trillion-scale corpus with hevay backbones, thus possessing certain cross-domain adaption capabilities. Others ( Wang et al. 2025c ; Woo et al. 2024 ) have specific structures,

which excels at capturing cross-domain features. However, their capabilites come from single time modality and lack explict domain knowledge guidance, thus hindering the performance. For end-to-end multimodal supervised models ( Jin et al. 2024 ; Liu et al. 2025a ) , though they consider the multimodal knowledge to enhance the domain-specific forecasting, they lack the ability to support zero-shot forecasting in cross-domain scenarios. In our view, the aurora of next-generation time series foundation model lies in pretraining a cross-modality model on cross-domain time series corpus, which can utilize the domain knowledge within modalities and serve as a versatile out-of-box forecaster in complex scenarios.

See Figure 1 , we propose Aurora by pionnering the exploration of multimodal time series foundation model. Specifically, we pretrain Aurora on Cross-Domain Multimodal Time Series Corpus, with time series data and sample-wise domain-specific text descriptions. Since previous works ( Chen et al. 2024a ; Yu et al. 2025 ) point out the endogenous images of time series contain additional geometric information, we also consider them into cross-modality learning. Considering the model architecture, Aurora adopts a novel cross-modality Encoder. Taking pretrained Bert ( Devlin et al. 2019 ) and ViT ( Liu et al. 2021 ) as modality encoders, Aurora then adopts token distillation to extract the key information in different modalities. To effectively model the cross-modality interaction, we propose a novel Modality-Guided Self-Attention Mechanism to utilize the external domain knowledge to adjust the attention of internal information within the time series data to obtain temporal features, and then fuse them with text and image features.

In the Aurora Decoder, we devise a novel flow-matching to fully utilize the fused cross-modality features to support multimodal cross-domain generative probabilistic forecasting. First, we use a ConditionDecoder to generate multimodal conditions for flow matching. Since the future trend of time series is often implied by external text information, and the inherent periodicity of time series is often contained in the endogenous images, we then design a Prototype Bank initialized by Period and Trend prototypes, and leverage a PrototypeRetriever to retrieve the “future prototypes” based on the inherent domain knowledge from texts and images. Compared with DDPM ( Ho et al. 2020 ) , Flow Matching ( Lipman et al. 2023 ) serves as a stochastic interpolant, which can start from a random distribution instead of a gaussian noise, with more flexibilities. So we take the generated future prototypes as starting points, which contains the rudiments of periodicity and trend for future tokens, thus can simplify the flow matching process. Our contributions are summarized as:

We propose a multimodal time series foundation model, called Aurora, which is pretrained on cross-domain multimodal time series corpus and supports generative probabilistic forecasting. Through effectively fusing multimodal information during pretraining, Aurora serves as a strong zero-shot forecaster, and can make accurate cross-domain inference.

We devise a novel cross-modality encoder in Aurora, consisting of token distillation and modality guiding, implemented by merticulously-designed attention structures. It can enhance the temporal representations while effectively fusing representations from texts and images.

We design a novel flow-matching process in the Aurora Decoder. It obtains multimodal conditions through a Transformer, and obtains future prototypes containing periodic and trend information as the starting points, thus enhancing the ability of flow-matching.

Experimentally, Aurora achieves state-of-the-art performance on three well-recognized benchmarks, including datasets from TimeMMD ( Liu et al. 2024b ) , TSFM-Bench ( Li et al. 2025c ) and ProbTS ( Zhang et al. 2024 ) , covering both unimodal and multimodal scenarios, thus demonstrating a strong out-of-box tool of decision intelligence.


## 2 Related works


## 2.1 Time Series Forecasting

Time Series Forecasting is vital in decision-making and has fascinated people for decades of years, which facilitates the emergence of a series of works. In recent years, deep-learning models are widely studied, among them, Autoformer ( Wu et al. 2021 ) , Triformer ( Cirstea et al. 2022 ) , TimesNet ( Wu et al. 2023 ) , Pathformer ( Chen et al. 2024b ) , PatchTST ( Nie et al. 2023 ) , Dlinear ( Zeng et al. 2023 ) , FiTS ( Xu et al. 2024 ) , SparseTSF ( Lin et al. 2024a ) , PDF ( Dai et al. 2024a ) , DUET ( Qiu et al. 2025d ) , and TimeMixer++ ( Wang et al. ) , continuously advancing the state-of-the-arts. However, though they possess the capabilities to extract the inherent dynamics in raw time series data, they only adapt to unimodal end-to-end forecasting scenarios, and often fall short in multimodal forecasting scenarios where the domain knowledge is widely contained in the text modality.

Recently, some works are proposed to explore the multimodal end-to-end supervised models. In summary, they utilize Large Language Models’ strong reasoning capabilities to integrate textual domain knowledge to prompt temporal modeling. Among them, Unitime ( Liu et al. 2024c ) , Time-LLM ( Jin et al. 2024 ) and CALF ( Liu et al. 2025a ) utilize the endogenous textual descriptions as prompts, GTP4MTS ( Jia et al. 2024 ) , TATS ( Li et al. 2025d ) and TimeMMD ( Liu et al. 2024b ) supports exogenous textual domain knowledge. However, they do not possess generalization capabilities in zero-shot scenarios.


## 2.2 Time Series Foundation Models

To support cross-domain generalization, unimodal Time Series Foundation Models are widely studied. The majority of them adopt Tranformer-based architectures, which are pretrained on time series corpus of billion- or trillion- scale to obtain the strong generalization capabilities. Among them, Sundial ( Liu et al. 2025d ) , VisionTS ( Chen et al. 2024a ) , ROSE ( Wang et al. 2025c ) , Time-MoE ( Shi et al. 2024b ) , MOIRAI ( Woo et al. 2024 ) , Chronos ( Ansari et al. ) , UniTS ( Gao et al. 2024 ) , Timer ( Liu et al. 2024d ) , and TimesFM ( Das et al. 2024 ) demonstrate strong zero-shot forecasting performance on unimodal tasks, even outperforming those full-shot supervised models in many cases. Considering the forecasting paradigm, Sundial, MOIRAI, Chronos, and Lag-Llama ( Rasul et al. 2023 ) also support probabilistic forecasting, which provides additional robustness and versatility for decision-making. Despite their endeavors to enhance cross-domain generalization capabilities, when historical series exhibit similarities, the forecasts they generate remain static. This lack of adaptability renders them unable to accommodate the diverse and changing real-world domains.

In this work, we propose Aurora to pioneer the exploration of multimodal time series foundation models. Through pretraining on Cross-Domain Multimodal Time Series Corpus, Aurora can extract the key domain knowledge within the text and image modalities to enhance the modeling of temporal features. Aurora also supports generative probabilistic forecasting, thus covering versatile tasks, including unimodal, multimodal, deterministic and probabilstic forecasting.


## 3 Aurora

In this work, we pretrain Aurora in a cross-modality paradigm, which adopts Channel-Independence ( Nie et al. 2023 ) on time series data, and models corresponding multimodal interaction to inject domain knowledge. Note that each variable of time series is first normalized through Instance Normalization ( Ulyanov et al. 2016 ) to mitigate the value discrepancy. See Figure 2 , Aurora mainly consists of two phases: 1) in Aurora Encoder, we tokenize and encode each modality into modal features, then fuse them to form multimodal representations; 2) in Aurora Decoder, we utilize a Condition Decoder to obtain the multimodal conditions of future tokens, leverage a Prototype Retreiver to retrieve the future prototypes based on the domain knowledge, and conduct flow matching on them to make generative probabilistic forecasts.


## 3.1 Encoding

Our proposed Aurora inherits the strong encoding capabilities from ViT ( Liu et al. 2021 ) and Bert ( Devlin et al. 2019 ) to extract the representations from images and texts, and adopts a temporal Channel-Independent Transformer as the main backbone. Therefore, inputs of all modalities are required to be tokenized first.

Given a univariate time series X ∈ ℝ T X\in\mathbb{R}^{T} , we adopt RevIN ( Kim et al. 2021 ) technique to mitigate the inherent non-stationarity of time series. The time series tokens X t ​ i ​ m ​ e X^{time} are formed through non-overlapped Patching and Embedding ( Cirstea et al. 2022 ; Nie et al. 2023 ) :

where Embedding is a linear projection, X t ​ i ​ m ​ e ∈ ℝ n t ​ i ​ m ​ e × d t ​ i ​ m ​ e X^{time}\in\mathbb{R}^{n^{time}\times d^{time}} are the embeded time series tokens, with n t ​ i ​ m ​ e n^{time} representations of dimension d t ​ i ​ m ​ e d^{time} .

To obtain the endogenous image tokens, we utilize the rendering techniques ( Chen et al. 2024a ) to make the transformation:

where the time series is first processed into 2D structure X 2 ​ D ∈ ℝ m × P X^{2D}\in\mathbb{R}^{m\times\mathrm{P}} based on the period P \mathrm{P} . Then the endogenous image X 3 ​ D ∈ ℝ 3 × w × h X^{3D}\in\mathbb{R}^{3\times w\times h} is rendered through repeating X 2 ​ D X^{2D} along channel dimension, and resizing into the standard input size of ViT. Finally, the image tokens X i ​ m ​ a ​ g ​ e ∈ ℝ n i ​ m ​ a ​ g ​ e × d i ​ m ​ a ​ g ​ e X^{image}\in\mathbb{R}^{n^{image}\times d^{image}} are obtained through ImagePatching and Embedding.

For the corresponding texts, the text tokens X t ​ e ​ x ​ t ∈ ℝ n t ​ e ​ x ​ t × d t ​ e ​ x ​ t X^{text}\in\mathbb{R}^{n^{text}\times d^{text}} can be easily obtained through tokenization, and retrievement from the vocabulary of Bert.

After obtaining the tokens from all the modalities, the hidden representations of texts and images are then generated through the pretrained VisionEncoder (ViT) and TextEncoder (Bert):

Inituitively, there exists informative redundancy in texts and images for multimodal time series forecasting. For texts as additional domain knowledge, key descriptions which can affect the future trend of time series often deserve only several words. For the endogenous image, we consider it as a technique to extract the varying inherent periodic information in time series data from multiple domains, where the information is also sparse. Therefore, we distill the tokens from text and image modalties to extract the key information and improve the efficiency:

where VisionDistiller and TextDistiller are based on the Multi-head Cross-Attention Mechanism. The R i ​ m ​ a ​ g ​ e ∈ ℝ K i ​ m ​ a ​ g ​ e × d i ​ m ​ a ​ g ​ e R^{image}\in\mathbb{R}^{K^{image}\times d^{image}} and R t ​ e ​ x ​ t ∈ ℝ K t ​ e ​ x ​ t × d t ​ e ​ x ​ t R^{text}\in\mathbb{R}^{K^{text}\times d^{text}} are learnable vectors, which are the queries and can serve as semantic clustering centriods ( Zhang & Yan 2022 ) to help compress the information in X ~ i ​ m ​ a ​ g ​ e \tilde{X}^{image} and X ~ t ​ e ​ x ​ t \tilde{X}^{text} . And X i ​ m ​ a ​ g ​ e \mathrm{X}^{image} and X t ​ e ​ x ​ t \mathrm{X}^{text} are the distilled image and text tokens.

In multimodal time series forecasting, the time modality occupies the dominant position and information from other modalities can serve as domain-specific knowledge to guide the extraction of temporal representations, thus enhancing the cross-domain generalization capability. In Aurora, we explicitly implement the above informative flow through a Modality-Guided Multi-head Self-Attention mechanism. First, we capture the correlations between the time modality and others through Cross-Attention based VisionGuider and TextGuider:

where VAttn and TAttn are unnormalized attention scores, separately denoting the correlations between time modality and image or text modality. Corr ∈ ℝ n t ​ i ​ m ​ e × n t ​ i ​ m ​ e \text{Corr}\in\mathbb{R}^{n^{time}\times n^{time}} denotes the inherent temporal correlations bridged through the cross-modality correlations. We also introduce W ∈ ℝ K i ​ m ​ a ​ g ​ e × K t ​ e ​ x ​ t W\in\mathbb{R}^{K^{image}\times K^{text}} as a learnable metric ( Qiu et al. 2025d ) to further tune the semantic distances. This process can help bridge the correlations between time series tokens through multimodal information, capable of leveraging domain knowledege to guided the modeling of temporal dynamics. We then inject Corr into the temporal encoding process:

where W Q , W K , W V ∈ ℝ d t ​ i ​ m ​ e × d t ​ i ​ m ​ e W^{Q},W^{K},W^{V}\in\mathbb{R}^{d^{time}\times d^{time}} . X t ​ i ​ m ​ e ∈ ℝ n t ​ i ​ m ​ e × d t ​ i ​ m ​ e \mathrm{X}^{time}\in\mathbb{R}^{n^{time}\times d^{time}} denotes the generated temporal representations. The Corr matrix contains domain knowledge, which can guide the attention scores to focus on the appropriate time series tokens. Finally, we fuse the representations from three modalities through a Cross-Attention based modality fuser:

where X f ​ u ​ s ​ e ∈ ℝ n t ​ i ​ m ​ e × d t ​ i ​ m ​ e \mathrm{X}^{fuse}\in\mathbb{R}^{n^{time}\times d^{time}} are the fused multimodal representations.


## 3.2 Decoding

Inspired by DiT ( Peebles & Xie 2023 ) , we utilize an L-stacked Transformer to decode the conditions of future tokens, which helps construct the stable Flow Matching process. Specifically, the ConditionDecoder consists of a Causal-Transformer and a Cross-Transformer:

where F F denotes the number of future tokens. The last token of X f ​ u ​ s ​ e \mathrm{X}^{fuse} is first copied F F times and fed to the Causal-Transformer to generate the future conditions X c ​ o ​ n ​ d ∈ ℝ F × d t ​ i ​ m ​ e X^{cond}\in\mathbb{R}^{F\times d^{time}} , then we adopt a Cross-Transformer integrated with RoPE ( Su et al. 2024 ) to further refine them into X c ​ o ​ n ​ d ∈ ℝ F × d t ​ i ​ m ​ e \mathrm{X}^{cond}\in\mathbb{R}^{F\times d^{time}} , where X f ​ u ​ s ​ e \mathrm{X}^{fuse} is set as Key and Value embeddings. Therefore, the ConditionDecoder can efficiently output all F F conditions.

Different from DDPM ( Ho et al. 2020 ) , which can be treated as an SDE solver to transform data from fixed Gaussian distributions to realistic target distributions, Flow Matching ( Lipman et al. 2023 ) serves as a more intuitive and smooth ODE solver, which learns the Velocity Field between a random initial distribution and the target distribution. However, current methods ( Liu et al. 2025d ; Kollovieh et al. ) still set the initial distributions as Standard Gaussian, which neglects the capability of Flow Matching to work like a stochastic interpolant. Obviously, constructing a propriate prototype as the inital starting point can enhance the intuitiveness and stability of Flow Matching.

Based on the motivation that the future trends and periodicities of time series mainly rely on the multimodal domain knowledge in texts and images, we inituitively devise a Prototype Bank and a PrototypeRetriever to adaptively construct initial prototypes for Flow Matching. The Prototype Bank 𝒫 ∈ ℝ M × p t ​ i ​ m ​ e \mathcal{P}\in\mathbb{R}^{M\times p^{time}} contains M M learnable period and trend prototypes, initialized through trigonometric, exponential, logarithmic, and polynomial bases. The Transformer-based PrototypeRetriever receives the text representations X ~ t ​ e ​ x ​ t \tilde{\mathrm{X}}^{text} and image representations X ~ i ​ m ​ a ​ g ​ e \tilde{\mathrm{X}}^{image} as inputs, considers the positional information of future tokens through Sinusoidal Embeddings ( Vaswani et al. 2017 ) , and outputs the categorical distributions of the all M M prototypes through Softmax:

where 𝒟 \mathcal{D} denotes the weights of prototypes, we then generate the new prototypes through: 𝒫 ~ = 𝒟 ⋅ 𝒫 ∈ ℝ F × p t ​ i ​ m ​ e \tilde{\mathcal{P}}=\mathcal{D}\cdot\mathcal{P}\in\mathbb{R}^{F\times p^{time}} , where the generated prototype 𝒫 ~ \tilde{\mathcal{P}} contains the approximate future periodicities and trends. As shown in Figure 3 , the motivation of Flow Matching is to fit the velocity field between the initial prototype y i ( 0 ) = 𝒫 ~ i + ϵ i y_{i}^{(0)}=\tilde{\mathcal{P}}_{i}+\epsilon_{i} and the target horizon y i ( 1 ) = y i y_{i}^{(1)}=\mathrm{y}_{i} , where y i ∈ ℝ p t ​ i ​ m ​ e \mathrm{y}_{i}\in\mathbb{R}^{p^{time}} is the groundtruth of the i i -th future token, and ϵ i ∼ 𝒩 ⁡ ( 0 , 𝐈 ) \epsilon_{i}\sim\mathcal{N}(0,\mathbf{I}) is used to increase the diversity during training. We design the Flow-Matching Network with an MLP structure and utilize the AdaLN ( Peebles & Xie 2023 ) to integrate the multimodal conditions h i = X i c ​ o ​ n ​ d h_{i}=\mathrm{X}^{cond}_{i} . We adopt the conditional optimal-transport path, which is energy-optimal and contributes to a uniform velocity field. And the function of Flow-Matching Network v t θ v^{\theta}_{t} is to predict the velocity based on the current position y i ( t ) y_{i}^{(t)} and condition h i h_{i} . To achieve this, the token-wise optimization objective ℒ \mathcal{L} is designed as:

where t ∈ [ 0 , 1 ] t\in[0,1] , y i ( 1 ) − y i ( 0 ) y_{i}^{(1)}-y_{i}^{(0)} denotes the targeted fixed velocity field. y i ( t ) = t ​ y i ( 1 ) + ( 1 − t ) ​ y i ( 0 ) y_{i}^{(t)}=ty_{i}^{(1)}+(1-t)y_{i}^{(0)} is the expected position in the uniform velocity field at moment t t . The objective is to tutor the Flow-Matching Network v t θ v^{\theta}_{t} to output the velocity when given the position and condition.

In the inference phase, the sampling process is a discretized integration process–see Algorithm 1 . The gaussian noise ϵ i ∼ 𝒩 ⁡ ( 0 , 𝐈 ) \epsilon_{i}\sim\mathcal{N}(0,\mathbf{I}) helps support probabilistic forecasting. Finally, we can obtain the forecasts y ^ i ∈ ℝ p t ​ i ​ m ​ e \hat{y}_{i}\in\mathbb{R}^{p^{time}} of the i i -th future token. And the forecasts of the future horizon are Y ^ = Concat ​ { y ^ i } ∈ ℝ F × p t ​ i ​ m ​ e \hat{Y}=\text{Concat}\{\hat{y}_{i}\}\in\mathbb{R}^{F\times p^{time}} .


## 4 Experiments

We make extensive experiments to evaluate the performance of Aurora. Specifically, we introduce the experimental settings in Section 4.1 . In Section 4.2 , we evaluate the zero-shot and few-shot performance of Aurora on multimodal forecasting scenarios. Considering the modal absence in the realistic world, we also evaluate the zero-shot performance of Aurora on unimodal forecasting scenarios–see Section 4.3 . To analyze the key components in Aurora, we also make detailed model analyses in Section 4.4 . In summary–see Figure 4 , our proposed Aurora achieves state-of-the-art performance in both unimodal and multimodal forecasting scenarios.


## 4.1 Experimental Settings

Cross-Domain Multimodal Time Series Corpus . We first collect a substantial number of open-source time series datasets across diverse domains, then generate the corresponding sample-wise textual descriptions using Large Language Model ( Liu et al. 2024a ) , which simulates the downstream scenarios with domain-specific textual information. The detailed method is introduced in Appendix A .

Benchmarks . We evaluate both the multimodal forecasting and unimodal forecasting performance of Aurora on well-recognized benchmarks, including TimeMMD ( Liu et al. 2024b ) , TSFM-Bench ( Li et al. 2025c ) , and ProbTS ( Zhang et al. 2024 ) . Note that these benchmarking datasets are strictly excluded from the pretraining time series corpus.

Baselines . We compare Aurora with 10 well-known unimodal time series foundation models, including Sundial ( Liu et al. 2025d ) , VisionTS ( Chen et al. 2024a ) , ROSE ( Wang et al. 2025c ) , Time-MoE ( Shi et al. 2024b ) , MOIRAI ( Woo et al. 2024 ) , TimesFM ( Das et al. 2024 ) , Timer ( Liu et al. 2024d ) , UniTS ( Gao et al. 2024 ) , Chronos ( Ansari et al. ) , and Lag-Llama ( Rasul et al. 2023 ) . We also consider 8 strong end-to-end supervised models, including multimodal ones like GPT4MTS ( Jia et al. 2024 ) , TATS ( Li et al. 2025d ) , CALF ( Liu et al. 2025a ) , and Time-VLM ( Zhong et al. ) , and unimodal ones like TSDiff ( Kollovieh et al. 2023 ) , CSDI ( Tashiro et al. 2021 ) , TimeGrad ( Rasul et al. 2021a ) , and GRU MAF ( Rasul et al. 2021b ) . The detailed information is provided in Appendix A .


## 4.2 Multimodal Forecasting

We compare the zero-shot forecasting performance of Aurora with unimodal Foundation Models, and compare the few-shot (10%) forecasting performance with Full-shot Multimodal End-to-end Supervised Models. As shown in Table 1 , compared with unimodal foundation models, Aurora obviously possesses stronger generalization capability by achieving most 1st counts. Compared with previous state-of-the-arts Sundial and VisionTS, Aurora achieves average MSE reduction of 27.0% and 31.2% on TimeMMD. When compared with Full-shot Multimodal End-to-end Supervised Models, Aurora is trained on only 10% of data and outperforms all baselines in most settings. Compared with well-known baselines like GPT4MTS and CALF, Aurora achieves average MSE reduction of 12.8% and 24.5% . On some datasets such as Climate and Environment, even the zero-shot performance of Aurora has outperformed those full-shot baselines. These empirical evidences can provide strong support of Aurora’s the multimodal generalization capability.


## 4.3 Unimodal Forecasting

Considering the modalilty absence phenomenon in many downstream scenarios, Aurora also supports forecasting without textual inputs through random masking in the pretraining phase. And endogenous images can be always obtained from raw time series. To evaluate the unimodal zero-shot forecasting performance, we conduct experiments on TSFM-Bench and ProbTS. As shown in Table 2 – 3 , Aurora achieves state-of-the-art performance on both deterministic and probabilistic forecasting tasks. Compared with Time-MoE and ROSE, Aurora achieves average MSE reduction of 15.1% and 22.9% on TSFM-Bench, demonstrating strong deterministic forecasting capability. When evaluated on probabilistic forecasting benchmark ProbTS, Aurora also outperforms CSDI and MOIRAI with average CRPS reduction of 21.5% and 38.3% . Aurora is proven the best-performed unimodal time series foundation model, ensuring the robustness when modality absence occurs.


## 4.4 Model Analysis

Ablation Studies. Based on the Modality-Guided Multi-head Self-Attention, Aurora can utilize the domain knowledge contained in text and image modalities to model the temporal features. To validate its effectiveness, we make ablations on it by setting Variant 1, which adopts original Multi-head Self-Attention. Considering the Prototype-Guided Flow Matching, which can generate prototypes of future tokens to simplify the generation process, we make Variant 2, which does not utilize the prototype mechanism and sets the initial distribution as Standard Gaussian. Naturally, we also make Variant 3, which eliminates both of them. As shown in Table 4 , results show that each above-mentioned module is indispensable, and a cascading effect occurs when both modules are removed, where the performance crashes when the modules are removed.

Inference Scability. Adopting a generative probabilistic head, Aurora makes forecasts based on multiple sampling–see Algorithm 1 . So that we study the scability of Prototype-Guided Flow Matching by exploring the correlations between the sampling number and forecasting performance in Figure 5 . Specifically, experiments are conduct on ProbTS, where the average values of CRPS and NMAE across all datasets are reported. The results indicate that both CRPS and NMAE demonstrate a consistent improvement as the sampling number rises. They attain good performance when the sampling number reaches 100 , showing obvious inference scability, and moderate efficiency–see Table 8 .


## 5 Conclusion

In this work, we propose a highly capable multimodal time series foundation model, named Aurora. To sum up, Aurora adopts a merticulously-designed modality fusion process, which encodes, distills, then injects multimodal domain knowledge through a Modality-Guided Self-Attention into the modeling of temporal dynamics. To enhance the forecasting performance, Aurora utilizes multimodal representations to generate conditions and prototypes of future tokens, which contributes to a novel Prototype-Guided Flow Matching, thus supporting generative probabilistic forecasting. Comprehensive experiments on unimodal and multimodal forecasting tasks demonstrate that Aurora is a strong out-of-box tool for decision intelligence.


## References


## The Use of Large Language Models (LLMs)

In this work, we only adopt Large Language Models in our methodology and data generation. Specifically, we leverage Bert as the TextEncoder of Aurora to extract the textual features. To generate the textual descriptions for the cross-domain multimodal time series corpus, we provide domain descriptions and raw time series for GPT4, encouraging it generate the descriptions of data characteristics, which are only used for pretraining Aurora. Note that we do not use Large Language Models in writing.


## Appendix A Experimental Details


## A.1 Cross-domain Multimodal Time Series Corpus

Cross-Domain Time Series Corpus. To pretrain Aurora, we initially make use of an extensive compilation of time series datasets. These datasets are sourced from multiple origins, encompassing specific subsets from repositories such as ERA5 ( Liu et al. 2025d ) , IoT ( Liu et al. 2025d ) , Monash ( Godahewa et al. 2021 ) , UEA ( Bagnall et al. 2018 ) , and UCR ( Dau et al. 2019 ) , as well as several well-established benchmarks ( Zhang et al. 2017 ; Wang et al. 2024 ; Liu et al. 2022 ; McCracken & Ng 2016 ; Taieb et al. 2012 ) . A comprehensive list of these datasets is presented in Figure 6 , containing more than 1 billion time series points. We take care to ensure that there is no overlap between the pre-training datasets and those employed in downstream evaluations. It should be noted that while both the pre-training and target sets incorporate weather, Energy, Health, and Economy data, they are from different sources.

Textual Descriptions. Since multimodal time series data is scarce in the real world, current works ( Liu et al. 2024b ; Kong et al. 2025 ; Xie et al. 2024 ) often construct corresponding textual information based on human experiences and Large Language Models, which is proven effective in training models. Following their paradigm, we provide raw time series data in Figure 6 with domain descriptions, encouraging GPT4 ( Achiam et al. 2023 ) to heuristically generate textual descriptions of sample-wise time series, thus obtaining high-quality multimodal time-series data from simulation. As shown in Figure 7 , here’s a sample of our prompt for GTP4 and the generated text:


## A.2 Baselines

For zero-shot forecasting, we compare Aurora against 10 advanced foundation models: Sundial ( Liu et al. 2025d ) , VisionTS ( Chen et al. 2024a ) , ROSE ( Wang et al. 2025c ) , Timer ( Liu et al. 2024d ) , MOIRAI ( Woo et al. 2024 ) , Chronos ( Ansari et al. ) , TimesFM ( Das et al. 2024 ) , Time-MoE ( Shi et al. 2024b ) , UniTS ( Gao et al. 2024 ) , and Lag-Llama ( Rasul et al. 2023 ) . In probabilistic forecasting and multimodal forecasting tasks, we also compare Aurora with 8 End-to-end supervised models: GPT4MTS ( Jia et al. 2024 ) , TATS ( Li et al. 2025d ) , CALF ( Liu et al. 2025a ) , Time-VLM ( Zhong et al. ) , TSDiff ( Kollovieh et al. 2023 ) , TimeGrad ( Rasul et al. 2021a ) , CSDI ( Tashiro et al. 2021 ) , and GRU MAF ( Rasul et al. 2021b ) . The corresponding codebases and implementation details are summarized in Table 5 .


## A.3 Benchmarks

To thoroughly assess the effectiveness of Aurora, we conduct comprehensive experiments on TimeMMD ( Liu et al. 2024b ) , TSFM-Bench ( Li et al. 2025c ) and ProbTS ( Zhang et al. 2024 ) . Our evaluation spans 9 multimodal and 11 unimodal forecasting datasets.

For multimodal forecasting, we use Agriculture, Climate, Economy, Energy, Environment, Health, Security, Social Good, and Traffic. For most datasets, the prediction length is set to L ∈ { 6 , 8 , 10 , 12 } L\in\{6,8,10,12\} , while Energy and Health use L ∈ { 12 , 24 , 36 , 48 } L\in\{12,24,36,48\} , and Environment uses L ∈ { 48 , 96 , 192 , 336 } L\in\{48,96,192,336\} .

For unimodal forecasting, we adopt ETTm1, ETTm2, ETTh1, ETTh2, Weather, Electricity, Traffic, Exchange, PEMS08, Solar, and Wind from ProbTS and TSFM-Bench. The prediction length is set to L ∈ { 96,192,336,720 } L\in\{96,192,336,720\} , and the specific evaluation settings are different in ProbTS and TSFM-Bench.

All models are configured with the contextual length that yields the best performance as recommended in their respective papers. It is crucial to note that, for datasets such as ETTh1 and Traffic, which are shared between TSFM-Bench and ProbTS, the evaluation settings, particularly strides, differ. A summary of the dataset statistics can be found in Table 6 .


## A.4 Experimental Settings

In the training of Aurora, we utilize Distributed Data Parallel within the PyTorch framework, as referenced in ( Paszke et al. 2019 ) . Due to the limited computational resources, all experiments are executed on only 8 NVIDIA A800 GPUs, each equipped with 80GB of GPU memory, which takes about 30 days to train Aurora from scratch. The model is optimized by the AdamW optimizer, with an initial learning rate of 5 × 10 − 5 5\times 10^{-5} . To gradually decrease the learning rate throughout the training process, we implement a step decay schedule through the StepLR scheduler. The code bases described above are incorporated into the Huggingface framework. During the pre-training phase, we utilize 11 historical time series tokens and 4 prediction tokens, with a reference patch size of p = 48 p=48 . The batch size is configured to be 8,192.

In the context of downstream forecasting tasks, we implement periodic patching strategies that are tailored to the temporal characteristics of each dataset. The quantity of past tokens is maintained at a constant value of 11.

Furthermore, we tackle the “Drop Last” issue, which has been emphasized in recent research works ( Qiu et al. 2024 ; Qiu et al. 2025c ; Li et al. 2025c ) . Specifically, when drop_last is set to True during test evaluation, it may yield misleading outcomes because of incomplete batches. To uphold consistency and fairness, we configure drop_last as False for all baseline models within our experimental setup.


## A.5 Evaluation Metrics

With respect to evaluation metrics, in accordance with the experimental setup in TSFM-Bench and TimeMMD, for deterministic forecasting, we employ the Mean Squared Error (MSE) and Mean Absolute Error (MAE) as evaluation metrics. In the context of probabilistic forecasting, within ProbTS, we utilize the Continuous Ranked Probability Score (CRPS) and Normalized Mean Absolute Error (NMAE). Consider the scenario featuring K K variates and a forecasting horizon of T T .

The Mean Squared Error (MSE) serves to quantify the average of the squared discrepancies between the predicted values and their respective ground truth values. The squaring operation within the calculation of MSE results in a more substantial penalty for larger errors. This characteristic renders the MSE highly sensitive to outliers. In a formal sense, the Mean Squared Error is defined as follows:

where K K denotes the number of variables, T T the prediction horizon, x t k x^{k}_{t} the true value, and x ^ t k \hat{x}^{k}_{t} the predicted value.

The Mean Absolute Error computes the average magnitude of prediction errors, disregarding their direction. By concentrating on the absolute differences, the MAE offers a robust and interpretable metric of accuracy.

where all terms adhere to the same definition as stated above. In contrast to Mean Squared Error (MSE), Mean Absolute Error (MAE) accords equal treatment to all errors and exhibits lower sensitivity to substantial deviations.

The CRPS evaluates the quality of probabilistic forecasts by contrasting the predicted cumulative distribution function (CDF) F F with the observed outcome x x . The calculation is as follows:

where 𝕀 { x ≤ z } \mathds{I}\{x\leq z\} represents the indicator function. The Continuous Ranked Probability Score (CRPS) rewards distributions that assign a high probability to the true value and attains its minimum when the predicted distribution coincides with the true distribution. In practical applications, we approximate the CRPS by utilizing the empirical Cumulative Distribution Function (CDF) F ^ ( z ) = 1 n ∑ i = 1 n 𝕀 { X i ≤ z } \hat{F}(z)=\frac{1}{n}\sum_{i=1}^{n}\mathds{I}\{X_{i}\leq z\} , which is based on n = 100 n=100 samples drawn from the conditional predictive distribution p θ ​ ( 𝒙 t | 𝒉 t ) p_{\theta}(\bm{x}_{t}|\bm{h}_{t}) .

The NMAE is an extension of the MAE. It normalizes the MAE with respect to the total magnitude of the ground-truth values. This normalization process facilitates a fair comparison across datasets that have different scales. The formula for NMAE is as follows:


## A.6 Model Configurations


## A.7 Efficiency Analysis


## Appendix B Full Results


## Appendix C Related Works

Time series forecasting (TSF) predicts future observations based on historical observations. Studies have shown that learned features may perform better than human-designed features ( Qiu et al. 2025b ; Qiu et al. 2025a ; Liu et al. 2025a ; Lu et al. 2023 ; Lu et al. 2024a ; Lu et al. 2024b ; Li et al. 2025a ; Yang et al. 2024 ; Zhou et al. 2025 ; Li et al. 2025b ; Wang et al. 2025a ; Wu et al. 2025c ; Wu et al. 2025a ; Wu et al. 2024 ; Qiu et al. 2025c ; Wu et al. 2025b ; Qiu et al. 2025e ; Dai et al. 2024c ; Hu et al. 2025a ; Dai et al. 2024d ; Liu et al. 2025c ; Sun et al. 2025b ; Sun et al. 2025a ; Niu et al. 2025 ) . Leveraging the representation learning of deep neural networks (DNNs), many deep learning-based methods emerge. TimesNet ( Wu et al. 2023 ) and SegRNN ( Lin et al. 2023 ) model time series as vector sequences, using CNNs or RNNs to capture temporal dependencies. Additionally, Transformer architectures, including Informer ( Zhou et al. 2021 ) , Dsformer ( Yu et al. 2023 ) , TimeFilter ( Hu et al. 2025b ) , TimeBridge ( Liu et al. 2025b ) , PDF ( Dai et al. 2024b ) , Triformer ( Cirstea et al. 2022 ) , PatchTST ( Nie et al. 2023 ) , ROSE ( Wang et al. 2025c ) , LightGTS ( Wang et al. 2025b ) , and MagicScaler ( Pan et al. 2023 ) capture complex relationships between time points more accurately, significantly improving forecasting performance. MLP-based methods, including DUET ( Qiu et al. 2025d ) , AMD ( Hu et al. 2025a ) , SparseTSF ( Lin et al. 2024a ) , CycleNet ( Lin et al. 2024b ) , NLinear ( Zeng et al. 2023 ) , and DLinear ( Zeng et al. 2023 ) , adopt simpler architectures with fewer parameters but still achieve highly competitive forecasting accuracy.