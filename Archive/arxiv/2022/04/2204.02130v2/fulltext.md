## SemanticCAP: Chromatin Accessibility Prediction Enhanced by Features Learning from a Language Model

A large number of inorganic and organic compounds are able to bind DNA and form complexes, among which drug-related molecules are important. Chromatin accessibility changes not only directly affects drug-DNA interactions, but also promote or inhibit the expression of critical genes associated with drug resistance by affecting the DNA binding capacity of TFs and transcriptional regulators. However, Biological experimental techniques for measuring it are expensive and time consuming. In recent years, several kinds of computational methods have been proposed to identify accessible regions of the genome. Existing computational models mostly ignore the contextual information of bases in gene sequences. To address these issues, we proposed a new solution named SemanticCAP. It introduces a gene language model which models the context of gene sequences, thus being able to provide an effective representation of a certain site in gene sequences. Basically, we merge the features provided by the gene language model into our chromatin accessibility model. During the process, we designed some methods to make feature fusion smoother. Compared with other systems under public benchmarks, our model proved to have better performance.chromatin accessibility; drug design; language model; transformer; feature fusion


## 1 Introduction

In human cells, genetic and regulatory information is stored in chromatin, which is deoxyribonucleic acid (DNA) wrapped around histones. Chromatin structure has a lot to do with gene transcription, protein synthesis, biochemical processes and other complex biological expressions. Among them, binding of small organic and inorganic molecules to DNA can influence numerous biological processes in which DNA participate. In particular, many anticancer, antibiotic, and antiviral drugs exert their primary biological effects by reversibly interacting with nucleic acids. Therefore, the study of its structure can help us design drugs to control gene expression and cure diseases ( Aleksić and Kapetanović 2014 ) . Some regions of the chromatin are open to transcription factors (TFs), RNA polymers (RNAPs), drug molecules and other cellular materials, while others are tightly entangled together and do not play a part in most cellular processes. These two regions of the chromatin are called open regions and closed regions, which are also known as accessibility and inaccessibility separately ( Wang et al. 2016 ) . Measuring it can generate clues to gene function that help to identify appropriate targets for therapeutic intervention. Meanwhile, monitoring changes in chromatin accessibility can help track and understand drug effects. Gallon et al. 2021 find that chromatin accessibility changes at intergenic regions are associated with ovarian cancer drug resistance. Another example is the chromatin opening (increased accessibility) of the targeted DNA satellites can explain how DNA-binding pyrrole-imidazole compounds that target different Drosophila melanogaster satellites leading to gain- or loss-of-function phenotypes ( Janssen et al. 2000 ) . In recent years, many high-throughput sequencing technologies have been used for the detection of open regions, such as DNase-seq ( Song and Crawford 2010 ) , FAIRE-seq ( Simon et al. 2012 ) and ATAC-seq ( Buenrostro et al. 2015 ) . However, biological experimental methods are costly and time-consuming, thus cannot be applied to large-scale chemical examinations. These restrictions have promoted the development of calculation methods.

Alongside the progress in computer science, several kinds of sequence-based calculation methods have been proposed to identify functional regions. Simply we can divide them into traditional machine learning methods ( Lee et al. 2011 ; Ghandi et al. 2014 ; Beer 2017 ; Xu and Strick 2021 ; Kumar and Bucher 2016 ) and neural network methods ( Alipanahi et al. 2015 ; Zhou and Troyanskaya 2015 ; Min et al. 2017 ; Liu et al. 2018 ; Guo et al. 2020 ) . Machine learning methods are mainly based on support vector machines (SVM). Lee et al. 2011 designed a SVM method based on k-mer features, which is defined as a segment of length k k . This method recognizes enhancers in mammalian cells. Subsequently, the gkm-SVM (gapped k-mers SVM) posed by Ghandi et al. 2014 exploited a feature set called interval k-mer features to improve the accuracy and stability of recognition. In recent years, with the rapid development of neural networks and the emergence of various deep learning models, a growing number of deep network models are used to solve such problems, where convolutional neural networks (CNNs) ( Kalchbrenner et al. 2014 ) and recurrent neural networks (RNNs) ( Hochreiter and Schmidhuber 1997 ) dominate. DeepBind ( Alipanahi et al. 2015 ) in 2015 and DeepSEA ( Zhou and Troyanskaya 2015 ) in 2017 got a significant performance improvement compared with traditional SVM-based methods after applying CNNs to modeling the sequence specificity of protein binding. Min et al. 2017 utilized the long short-term memory network (LSTM) to predict the chromatin accessibility and achieved state-of-the-art at the time, thus proving the effectiveness of RNNs for DNA sequence problems.

However, we point out that the previous methods have the following shortcomings at least. First, most of the previous methods are based on k-mer, that is, a segment of length k k . Specifically, it takes a segment of length k k at intervals. The artificial division of the original sequence may destroy the inside semantic information and cause difficulty in the learning of subsequent models. Second, with the progress of language models, we have the ability to learn the interior semantic information of sequences through pre-training. There have been related works in existed methods, such as Min et al. 2017 using Glove ( Pennington et al. 2014 ) to train the word vectors of k-mer. However, these pre-train models are mostly traditional word vector methods. On the one hand, they can only learn the characteristics of the word itself and have no knowledge of the context of DNA sequences ( Sun et al. 2019 ) . On the other hand, they are limited to a specific dataset thus cannot be widely applied to other scenarios. Third, traditional CNNs and RNNs have been proved to be unsuitable for long-sequence problems ( Bengio et al. 2013 ) . CNNs restricted by the size of convolution kernels fail in learning global information effectively, while RNNs tend to cause gradient disappearance and slow training due to the lack of parallelizability when getting a long input. In contrast, the attention mechanism (Attention) ( Vaswani et al. 2017 ) can effectively learn the long-range dependence of sequences, which has been widely used in the field of natural language processing.

In response to the above disadvantages, we constructed a chromatin accessibility prediction model based on features learning from a language model. A implemention of our system is available at github.com/ykzhang0126/SemanticCAP . Our method has at least the following three improvements:

A DNA language model is utilized to learn the deep semantics of DNA sequences, and introduces the semantic features in the process of chromatin accessibility prediction. Therefore we obtain additional complex environmental information.

Both the DNA language model and the chromatin accessibility model use character-based input instead of k-mer which stand for segments of length k k . The strategy prevents the information of original sequences from being destroyed.

The attention mechanism is widely used in our models in place of CNNs and RNNs, which can make the model more powerful and stable in handling long sequences.

Before formally introducing our method, we first present some preliminary knowledge, including some common sense information, theorems and corollaries.


## 2 Theories

For two standardized distributions using layer normalization (LN), which are denoted as X 1 X_{1} and X 2 X_{2} , the concat of them, that is, X ≡ [ X 1 , X 2 ] X\equiv[X_{1},X_{2}] , is still a standardized distribution.

Suppose that X 1 X_{1} has n n elements and X 2 X_{2} has m m elements. As we all know, LN ( Ba et al. 2016 ) transforms the distribution X X as

where μ \mu and σ \sigma are the expectation and standard deviation of X X , respectively. Obviously, for the normalized distribution X 1 X_{1} and X 2 X_{2} , we have

where E E stands for the expectation function and D D stands for the deviation function. The new distribution X X is derived by concating X 1 X_{1} and X 2 X_{2} , thus having n + m n+m elements. Inferring from Eq. 2 , we get

For X 1 X_{1} and X 2 X_{2} , we also know that

Substituting Eq. 2 and Eq. 3 into Eq. 6 and Eq. 7 , and finally into Eq. 5 , we get

Eq. 4 and Eq. 8 demonstrate the standardization of X X . ∎

For any two distributions X 1 X_{1} , X 2 X_{2} , there always exist two coefficients λ 1 \lambda_{1} , λ 2 \lambda_{2} , so that the concat of them after being multiplied by the two coefficients respectively, that is X ≡ [ λ 1 ​ X 1 , λ 2 ​ X 2 ] X\equiv[\lambda_{1}X_{1},\lambda_{2}X_{2}] , is a standardized distribution.

Suppose that X 1 X_{1} has n n elements and X 2 X_{2} has m m elements. We denote the expectation of the two distributions as μ 1 \mu_{1} , μ 2 \mu_{2} , and the variance as σ 1 2 \sigma_{1}^{2} , σ 2 2 \sigma_{2}^{2} . Notice that λ 1 \lambda_{1} and λ 2 \lambda_{2} are all scalars. Now pay attention to X X . To prove this theorem, we want X X to be a standardized distribution, which requires the expectation of X X to be 0 0 and the variance to be 1 1 . Therefore, we can list the following equation set.

At the same time, we have equations similar to Eq. 6 and Eq. 7 , that is

which is easy to calculate according to the nature of expectation and variance. Notice that Eq. 9 has two variables and two independent equations, meaning it should be solvable. By calculating Eq. 9 , we can get the numeric solution of λ 1 \lambda_{1} and λ 2 \lambda_{2} as follows.

The existence of Eq. 12 ends our proof. Actually, we get two sets of solutions here, for λ 1 \lambda_{1} can be either positive or negative, and so be λ 2 \lambda_{2} . The signs of λ 1 \lambda_{1} and λ 2 \lambda_{2} depend on the signs of μ 1 \mu_{1} and μ 2 \mu_{2} , which can be easily inferred from the first equation in Eq. 9 . ∎

For any distributions X 1 X_{1} , X 2 X_{2} , … \dots , X n X_{n} , there always exist n n coefficients λ 1 \lambda_{1} , λ 2 \lambda_{2} , … \dots , λ n \lambda_{n} , so that the concat of them after being multiplied by the n n coefficients respectively, that is X ≡ [ λ 1 ​ X 1 , λ 2 ​ X 2 , … , λ n ​ X n ] X\equiv[\lambda_{1}X_{1},\lambda_{2}X_{2},\dots,\lambda_{n}X_{n}] , is a standardized distribution.

The overall proof way is similar to that in Theorem 2 . Note that in this case, we have n n variables but only 2 2 independent equations, resulting in infinite solutions according to Eq. 9 . To be more precise, the degree of freedom of our solutions is n − 2 n-2 . ∎

In neural networks, for any two tensors X X , Y Y which satisfy E ⁡ ( X ) = E ⁡ ( Y ) = 0 E(X)=E(Y)=0 , the probability of feature disappearance of X X after concating and normalizing them is Ω ⁡ ( S ​ D ​ ( Y ) S ​ D ​ ( X ) ) \Omega(\frac{SD(Y)}{SD(X)}) , where S ​ D SD represents the standard deviation.

Feature disappearance is defined as a situation where the features are too small. Concretely, for a tensor X X and a threshold t F ​ D t_{FD} , if the result of a subsequent operation of X X is smaller than t F ​ D t_{FD} , the feature disappearance of X X happens. Here t F ​ D t_{FD} can be an arbitrarily small value, such as 10 − 5 10^{-5} .

Suppose that X X has n n elements and Y Y has m m elements. We denote the expectation of the two distributions as μ 1 \mu_{1} , μ 2 \mu_{2} , and the variance as σ 1 2 \sigma_{1}^{2} , σ 2 2 \sigma_{2}^{2} . As stated in the precondition, we already know

Let Z ≡ [ X , Y ] Z\equiv[X,Y] and Z ′ ≡ LN ⁡ ( Z ) ≡ [ X ′ , Y ′ ] Z^{\prime}\equiv\mathrm{LN}(Z)\equiv[X^{\prime},Y^{\prime}] . By the help of Eq. 9 , we have

We denote E ⁡ ( Z ) E(Z) as μ \mu and D ⁡ ( Z ) D(Z) as σ 2 \sigma^{2} . According to Eq. 1 , for X ′ X^{\prime} we know that

We denote E ⁡ ( X ′ ) E(X^{\prime}) as μ 1 ′ \mu_{1}^{\prime} and D ⁡ ( X ′ ) D(X^{\prime}) as σ 1 ′ 2 \sigma_{1}^{\prime 2} . Now we consider the result of a subsequent operation of X X , which is ∑ i = 1 n λ i ​ X i ′ \sum_{i=1}^{n}\lambda_{i}X_{i}^{\prime} . This is very common in convolution, linear or attention layers. For the result, an observation is

where λ m = max 1 ≤ i ≤ n | λ i | \lambda_{m}=\mathop{\max}\limits_{1\leq i\leq n}|\lambda_{i}| . For the convenience of analysis, all λ \lambda are set to 1. This will not bring loss of generality, because the value scaling from λ m \lambda_{m} to 1 has no effect in the subsequent derivation. Here we denote ∑ X ′ \sum X^{\prime} as S X ′ S_{X^{\prime}} . According to the central limit theorem (Lindeberg-Lévy form) ( Giné 1983 ) , we find that S X ′ S_{X^{\prime}} obeys a normal distribution, that is

For a feature disappearance threshold t F ​ D t_{FD} , We want to figure out the probability of | S X ′ | < t F ​ D |S_{X^{\prime}}|<t_{FD} . Denote this event as F ​ D FD and we can get

where Φ \Phi is the cumulative distribution function (cdf) of the standard normal distribution. Since it is an integral which does not have a closed form solution, we cannot directly analyze it. According to Eq. 13 , Eq. 14 and Eq. 16 , we know μ 1 ′ = 0 \mu_{1}^{\prime}=0 . At the same time we know that t F ​ D t_{FD} is a small number, leading to t F ​ D n ​ σ 1 ′ → 0 \frac{t_{FD}}{\sqrt{n}\sigma_{1}^{\prime}}\to 0 . Therefore, we have the equation as follows.

The formula is a Taylor expansion where φ \varphi is the probability density function (pdf) of the standard normal distribution, R 1 ​ ( x ) R_{1}(x) is the Lagrange remainder and o ⁡ ( x ) o(x) is the Peano remainder standing for a high-order infinitesimal of x x . Combining Eq. 15 , Eq. 17 , Eq. 20 and Eq. 21 , we cat get

where k s = m n k_{s}=\frac{m}{n} and k d = σ 2 σ 1 k_{d}=\frac{\sigma_{2}}{\sigma_{1}} . The above equation can also be written as P ⁡ ( F ​ D ) = Ω ⁡ ( S ​ D ​ ( Y ) S ​ D ​ ( X ) ) P(FD)=\Omega(\frac{SD(Y)}{SD(X)}) . ∎

In neural networks, feature disappearance can lead to gradient disappearance.

According to Theorem 2 , the feature disappearance happens if there exists a tensor T T such that | T | < t F ​ D |T|<t_{FD} . Similar to the definition of feature disappearance, gradient disappearance is defined as a situation where the gradients are too small. Concretely, for a parameter C C with the gradient of g ​ r ​ a ​ d C grad_{C} and a threshold t G ​ D t_{GD} , if g ​ r ​ a ​ d C grad_{C} is smaller than t G ​ D t_{GD} , the gradient disappearance of C C happens. Here t G ​ D t_{GD} can be an arbitrarily small value.

Consider a subsequent operation of T T , which is T ′ = C ​ T n T^{\prime}=CT^{n} , where n n stands for the number of layers involved in the calculation. The gradient disappearance happens if

At the same time, we already have | T | n < t F ​ D n |T|^{n}<t_{FD}^{n} , which means we just need to meet

Note that t F ​ D t_{FD} is a small number, which means t F ​ D < 1 t_{FD}<1 . Finally we derive a formula of n n .

Thereby we get a sufficient condition for n n and we can come to a conclusion. The disappearance of gradients occurs in layers deep enough after the disappearance of features. ∎

The above corollary is consistent with intuition. The disappearance of gradients is always accompanied by the disappearance of features, and it is always a problem in deep neural networks.

In neural networks, for any two tensors X 1 X_{1} , X 2 X_{2} of the same dimension, there always exist two matrices M 1 M_{1} , M 2 M_{2} , so that the operation of concating them and the operation of adding them after being multiplied in the Hadamard format by the two matrices respectively, are equivalent in effect.

First of all, we illustrate the definition of Hadamard product ( Horn 1990 ) . The Hadamard product (also known as the element-wise product) is a binary operation that takes two matrices of the same dimensions and produces another matrix of the same dimension. Concretely, we can define it as

The symbol ’ ∘ \circ ’ is used to distinguish from the more common matrix product, which is denoted as ’ ⋅ \cdot ’ and usually be omitted. The definition implies that the dimension of X 1 X_{1} should be the same as that of M 1 M_{1} , so are X 2 X_{2} and M 2 M_{2} . At the same time X 1 X_{1} and X 2 X_{2} are assumed to have the same dimension in the precondition of our proposition. So we might as well set them to ℝ R × N \mathbb{R}^{R\times N} . Now we give the representation of X 1 X_{1} and X 2 X_{2} .

Our goal is to weigh the effect of the two operations. For the convenience of comparison, we let the results after the two operations multiply a matrix, thus converting the dimension to ℝ R × M \mathbb{R}^{R\times M} . Adding a linear layer is very common in neural networks, and it hardly affects the network’s expression ability.

Considering the first scheme, the concat of X 1 X_{1} and X 2 X_{2} , we have

where A ∈ ℝ 2 ​ N × M A\in\mathbb{R}^{2N\times M} and U ∈ ℝ R × M U\in\mathbb{R}^{R\times M} . Observing the i i -th row and j j -th column of U U , we can find that

Considering the second scheme, with the addition of X 1 X_{1} and X 2 X_{2} as the core, we have

where B ∈ ℝ N × M B\in\mathbb{R}^{N\times M} and V ∈ ℝ R × M V\in\mathbb{R}^{R\times M} . Still we pay attention to the i i -th row and j j -th column of V V and find that

Comparing Eq. 29 and Eq. 31 , we find that when we let λ i ​ 1 T ∘ b j \lambda_{i1}^{T}\circ b_{j} equal to a j ​ p a_{jp} and λ i ​ 2 T ∘ b j \lambda_{i2}^{T}\circ b_{j} equal to a j ​ q a_{jq} , the values of U U and V V are equal, which is a strong evidence of effect equivalence. ∎

As the equivalence has been proved, the same as the plain concat no information is lost in the above method. We point out that the Hadamard product is an alternative version of the gate mechanism ( Liu and Perez 2017 ) . We use coefficients to adjust the original distribution to screen out effective features. For the speed and stability of training, it is recommended to set the initial value of M M to 1.

Further, we can observe the gradient of the parameters λ \lambda in Eq. 30 , we have

Compared with the gate mechanism, our method is simpler, space-saving, and more direct in gradient propagation.

Of course, Theorem 2 could be generalized to cases with arbitrary number of tensors. We describe it in the following corollary. {Corollary} In neural networks, for any tensors X 1 X_{1} , X 2 X_{2} , … \dots , X n X_{n} of the same dimension, there always exist n n matrices M 1 M_{1} , M 2 M_{2} , … \dots , M n M_{n} so that the operation of concating them and the operation of adding them after being multiplied in the Hadamard format by the n n matrices respectively, are equivalent in effect.

Similar to the proof of Theorem 2 . ∎

In neural networks, for a layer composed of n n neurons, the effective training times of the neurons in this layer reach the maximum when the dropout rate is set to 0 0 or 1 − 1 n 1-\frac{1}{n} .

The number of neurons in this layer is n n , so we shall mark them as N 1 N_{1} , N 2 N_{2} , … \dots , N n N_{n} . Suppose that the dropout rate ( Baldi and Sadowski 2013 ) is p p and the total number of training times is t t . We denote 1 − p 1-p as q.

Consider the t i t_{i} -th training. The network randomly selects n ​ q nq neurons for update due to the exisitence of dropout mechanism. Denote these neurons as N 1 N_{1} , N 2 N_{2} , … \dots , N n ​ q N_{nq} .

Without loss of generality, we consider the next time N 1 N_{1} is selected, which is the t 2 t_{2} -th training. We denote the number of neurons selected for update in N 2 N_{2} , … \dots , N n ​ q N_{nq} as S S , and the number of that selected in N n ​ q + 1 N_{nq+1} , … \dots , N n N_{n} as T T . Easily we know that the selection of neurons in S S is an independent event, so we have

At the same time, the relationship between S S and T T is

Inferring from Eq. 33 and Eq. 34 , we get

The neurons represented by S S are the neurons that are updated jointly at time t 2 t_{2} and time t 1 t_{1} , thus belong to the same sub-network. We assume that they share one training gain with N 1 N_{1} . At the same time, the neurons represented by T T have not been updated at time t 1 t_{1} , thus each of them has one unique training gain. Therefore, at the update time t 2 t_{2} , the expected gain of N 1 N_{1} is 1 × 1 E ⁡ ( T ) + 1 × 1 E ⁡ ( S ) + 1 1\times\frac{1}{E(T)+1}\times\frac{1}{E(S)+1} , which is derived from the above proportion analysis. Paying attention to t 1 t_{1} and t 2 t_{2} , we find that t 2 − t 1 t_{2}-t_{1} obeys a geometric distribution, because the selection of N 1 N_{1} is a Bernoulli experiment with probability q q . That is t 2 − t 1 ∼ 𝒢 ​ ℰ ​ ( q ) t_{2}-t_{1}\sim\mathcal{GE}(q) , meaning that

Therefore, the expected number of training times of N 1 N_{1} is E ⁡ ( t t 2 − t 1 ) = t ​ q E(\frac{t}{t_{2}-t_{1}})=tq . The total training gain is the product of the number of training times and the gain of a single training, which we denote as G G . Now the formula emerges.

Denote f ⁡ ( q ) f(q) as the denominator of G ⁡ ( q ) G(q) and differentiate that to get

With the help of Eq. 38 , it is easy to draw an image of G ⁡ ( p ) G(p) shown in Figure 1 where we set t t to 1 1 . The observation is that when q = 1 n q=\frac{1}{n} or q = 1 q=1 , that is, p p is 0 or 1 − 1 n 1-\frac{1}{n} , G G reaches the maximum value t n \frac{t}{n} , demonstrating the effective training times of N 1 N_{1} are the largest. The conclusion can be generalized to every neuron in the layer.

∎

In neural networks, if the amount of training data is sufficient, the optimal value of dropout rate is 0.5; if the amount of training data is insufficient, a number close to 1 is a better choice.

Theorem 2 focuses on the effective training times of neurons in the network, and the corollary focuses on the representation ability. It can be seen from Eq. 37 that the effective training times of a certain layer is directly proportional to the total training times t t . When the number of training times reaches a certain threshold, the network reaches a balance point, and further training will not bring any performance improvement.

If the training data are sufficient, which means t t and G G are large enough, the network is guaranteed to get fully trained. Therefore we do not need to worry about whether the training times of neurons in the network is enough. But we still need to consider the representation ability of the network, which has a close relationship with the number of sub-networks S ​ N SN . It can be calculated as

which is a combination number. Obviously, when p p is 0.5 0.5 , the number of sub-networks is the largest, and the network’s representation ability is relatively strong.

However, when the training data is not enough, we cannot guarantee the sufficiency of training. On the one hand, we need to set the dropout rate to a value close to 0 0 or 1 − 1 n 1-\frac{1}{n} to guarantee the number of training as Theorem 2 says. On the other hand, in order to ensure the network’s representation ability, we want the dropout rate be close to 0.5 0.5 . Here a balanced approach is to choose the turning point shown in Figure 1 , which considers both training times and representation ability. Because this point is difficult to analyze, we give a fitting function shown in Figure 1 , whose error is bounded by 2 × 10 − 2 2\times 10^{-2} for n n smaller than 512 512 . ∎

The above corollary is intuitive, because the complexity of the network should be proportional to the amount of data. Little data requires a simple model, calling for a higher dropout rate. Notice that a large dropout rate not only enables the model to be fully trained, but also helps to accelerate the process. In a modern neural network framework, the discarded neurons will not participate in the gradient propagation this time, which largely reduces the number of parameters need to be adjusted in the network.


## 3 Models

To address the task of chromatin accessibility prediction, we designed SemanticCAP, which includes a DNA language model shown in Section 3.1 and a chromatin accessibility model shown in Section 3.2 . Briefly, we augment the chromatin accessibility model with features provided by the DNA language model, thereby improving the performance of chromatin accessibility prediction. The detailed methods are described below.


## 3.1 DNA language model

We use the human reference genome GRCh37 (hg19) as the original data for our DNA language model. The human reference genome is a digital nucleic acid sequence database that can be used as a representative example of the gene set of an idealized individual of a species ( Pan et al. 2019 ) . Therefore, the model based on the database could be applied to various genetic-sequence-related issues.

The task we designed for our DNA language model is using context to predict the intermediate base. However, there are at least three challenges. First is that there are two inputs, the upstream and downstream, which are defined as the upper and lower sequence of a certain base. Since we predict the middle base from the information on both sides, the definition of the upstream and downstream are interchangeable, which means that the context should be treated in the same way. Second, the input is quite long, far from the length 4 4 of the output, which stands for the classification result of bases. The large gap between the input and output lengths leads to the fact that neural networks must be designed in a more subtle way, otherwise redundant calculations or poor results may occur. Third, we do not always have such long context data in real situations. For example, the length of upstreams in the DNA datasets in Table 1 mostly varies from 0 to 600, resulting in insufficient information in some cases.

To solve the above problems, we designed the simple but effective input format and training method. First of all, we randomly select a certain position, taking the upstream and downstream sequence with a length of 512 512 as the input, and the output is the base connecting the upstream and downstream, i.e. A \mathrm{A} , T \mathrm{T} , C \mathrm{C} , G \mathrm{G} .

For the first challenge, we combine the upstream and downstream into one sequence, separated by a special prediction token [ LOST ] \mathrm{[LOST]} , and provide different segment embeddings for the two parts. Also, a special classification token [ CLS ] \mathrm{[CLS]} is added to the beginning of the sequence to learn an overall representation of it. For the second challenge, the final hidden state corresponding to the token [ LOST ] \mathrm{[LOST]} is used as the aggregate sequence representation for classification tasks, by which the output dimension is reduced quickly without complex network structures. This technique was used in Bert ( Devlin et al. 2018 ) for the first time. For the third challenge, some data augmentation tricks are applied in order to enhance the capabilities of the model. First, we can construct symmetric sequences based on the principle of base complementation and the non-directionality of DNA sequences, including the axial symmetry and mirror symmetry. This helps the model learn the two properties of DNA sequences. Second, we do not provide complete input to the model, which helps to enhance the model’s prediction ability under insufficient information. Basically, we mask some percentage of the input tokens at random, and concretely there are two strategies. For a certain sequence, either upstream or downstream, we mask (replace with [ MASK ] \mathrm{[MASK]} ) 20 % 20\% of random tokens in 10 % 10\% of cases or 40 % 40\% of consecutive tokens in 15 % 15\% of cases. Figure 2 is an example below for our mask operation. In this case, 2 2 random tokens of the upstream and 3 3 consecutive tokens of the downstream are masked.

Finally, there is no need to worry about overfitting. First, we have 10 9 10^{9} bases in the DNA dataset, meaning that we will not over-learn some specific data. Second, we have mask and dropout operations in our training, which both are great ways to avoid over-training.

The input and output are constructed as described in Section 3.1.1 , and we denote them as T i ​ n T_{in} and T o ​ u ​ t T_{out} . Basically, the model can be described as

where embed \mathrm{embed} is the Input Embedding layer, multi − conv \mathrm{multi-conv} stands for our Multi-Kernel CNN, transformer \mathrm{transformer} represents the transformer blocks and mlp \mathrm{mlp} contains a Linear layer and a Softmax function. Figure 3 shows the full picture of the model.

embed \mathrm{embed} is the encoding layer transforming the input sequence into a matrix. The dimension conversion is ℕ L → ℝ L × E \mathbb{N}^{L}\xrightarrow{}\mathbb{R}^{L\times E} , Where L L is the length of the sequence and E E is the encoding length. Specifically, we encode the input as

where word − embed \mathrm{word-embed} is the meaning of the word itself, position − embed \mathrm{position-embed} provides the representation of different positions and segment − embed \mathrm{segment-embed} distinguishes the upstream and the downstream. An intuitive approach is concating the three encodings without loss of semantics. But this cost triple space. Instead, we directly add these three encodings. This works because the three parameters are all leaf nodes of the training graph, which can automatically adapt to each other’s distribution. By this way we reduce the dimension of the coded matrix, thus reducing the parameter space and data space.

multi − conv \mathrm{multi-conv} is the multi-kernel convolution layer learning a short-range relationship of the sequence. The dimension conversion is ℝ L × E → ℝ L × H \mathbb{R}^{L\times E}\xrightarrow{}\mathbb{R}^{L\times H} , where H H is the hidden dimension. Here, we use convolution kernels of different lengths to learn local relationships at different distances, and propose a smooth feature addition (SFA) method to fuse these features. Specifically, we do

where conv i \mathrm{conv}_{i} is a normal one-dimensional convolution layer with a kernel length of l i l_{i} , whose output dimension is ℝ L × H \mathbb{R}^{L\times H} , λ i \lambda_{i} is a network parameter with a dimension of ℝ L × H \mathbb{R}^{L\times H} and k k is the number of kernels of different lengths. The sizes of convolution kernels are small rather than large ones, whose advantages have been verified in DenseNet ( Huang et al. 2017 ) . On the one hand, small convolution kernels use less space than large convolution kernels. On the other hand, we need small convolution kernels to learn the local information of the sequence, while the long-range dependence of the sequence is to be explored by the subsequent transformer \mathrm{transformer} module.

Now we explain how we designed the smooth feature addition algorithm SFA. Before that, we have to take an insight into what happens in the plain concat of features.

In a sequence problem, we often directly concat two features in the last dimension. Specifically, if we have two features with dimensions ℝ L × M \mathbb{R}^{L\times M} and ℝ L × N \mathbb{R}^{L\times N} , the dimension of the features after concat is ℝ L × ( M + N ) \mathbb{R}^{L\times(M+N)} . We thought that this approach would not lose information, but in fact there is a danger of feature disappearance. For two features of different distributions learning from different modules, plain concat will bring an unbalanced distribution, where some values are extremely small. To make matters worse, layer normalization is usually used to adjust the distribution after a concat operation, making the values to be concentrated near 0 0 . Quantitative analysis can be seen in Theorem 2 . Finally, as the network goes deeper, the gradient disappears, leading to the difficulty of learning. This is proven in Corollary 2 .

A naive thought is to normalize the two distributions before concating them, which proves to be correct in Theorem 2 . However, it’s not effective, for it converts the dimension from ℝ L × H \mathbb{R}^{L\times H} to ℝ L × k ​ H \mathbb{R}^{L\times kH} , posing a challenge for the subsequent module design. Considering that the dimensions of convolution features are the same, inspiring us to find a way to smoothly add them using some tuning parameters. That’s how we designed SFA. Corollary 2 proves the equivalence of SFA and plain concat, and illustrates the working mechanism of SFA and its advantages in space occupation, feature selection and gradient propagation.

transformer \mathrm{transformer} is the stack of transformer blocks learning a long-range relationship of the sequence. The dimension conversion is ℝ L × H → ℝ L × H \mathbb{R}^{L\times H}\xrightarrow{}\mathbb{R}^{L\times H} . Simply it can be described as

where sub ⁡ ( f , x ) = LN ⁡ ( x + f ⁡ ( x ) ) \mathrm{sub}(f,x)=\mathrm{LN}(x+f(x)) . ff \mathrm{ff} represents the feed forward function and attention \mathrm{attention} is short for multi-head attention. The module is proposed by Vaswani et al. 2017 .

mlp \mathrm{mlp} is the output layer, responsible for converting the hidden state to the output. The dimension conversion is ℝ L × H → ℕ \mathbb{R}^{L\times H}\xrightarrow{}\mathbb{N} . We extract the tensor corresponding to the token [ LOST ] \mathrm{[LOST]} , convert it into an output probability through a linear layer, and generate the prediction value via a softmax function. The output process is


## 3.2 Chromatin accessibility model

We select DNase-seq experiment data of six typical cell lines as the original data for our chromatin accessibility model, including GM12878, K562, MCF-7, HeLa-S3, H1-hESC and HepG2. GM12878 is a type of lymphoblast, produced by EBV transformation from the blood of a female donor of Northern European and Western European descent. K562 is an immortalized cell derived from a female patient with chronic myeloid leukemia (CML). MCF-7 is a breast cancer cell sampled from a white female. HeLa-S3 is an immortal cell derived from a cervical cancer patient. H1-hESC is a human embryonic stem cell. HepG2 comes from a male liver cancer patient.

For each cell type, we downloaded the original sequence data from the ENCODE website, use a short read aligner tool bowtie ( de Ruijter and Guldenmund 2016 ) to map the DNA sequence to the human reference genome (hg19), and use HOTSPOT ( John et al. 2011 ) to identify chromatin accessibility regions (peaks). We treat these variable-length sequences as positive samples. At the same time, we sample the same number and same size sequences from the whole genome as negative samples. An overview of the data is shown in Table 1 , which shows the number of sequences, the minimum value, the median value, the maximum value and the standard deviation of lengths. Also, the distribution statistics of different datasets are shown in Figure 4 . For the fairness of comparison, we removed sequences with length less than 36 36 . We truncate or expand each sequence symmetrically to a sequence of length 768 768 , and take a context of length 512 512 for each site in it. Similar to our DNA language model, a special classification token [ CLS ] \mathrm{[CLS]} is added to the beginning of the sequence to predict the accessibility. Therefore the actual input length of our model is 768 + 512 × 2 + 1 = 1793 768+512\times 2+1=1793 . From Figure 4 , we observe that most of the lengths are clustered between 36 36 and 1792 1792 . This proves that our cut-off has little impact and is reasonable. Compared with the input length 800 800 in Min et al. 2017 , our prediction length has increased by 124 % 124\% , and the quantity of DNA sequences that do not need to be truncated in the original dataset has increased by 17.4 % 17.4\% . Moreover, we do not pay a great price for such a long input because our context is handed over to a pre-trained model to predict. The output is the accessibility of the input sequence, i.e., either 0 0 for inaccessibility or 1 1 for accessibility.

Finally, the ratio of our training set, validation set, and test set is 0.85 : 0.05 : 0.10 0.85:0.05:0.10 . The training set is used to train the model, the validation set is used to adjust the hyperparameters to prevent overfitting, and the test set is used to test the performance of the final model.

The input and output are constructed as described in Section 3.2.1 , and we denote them as T i ​ n T_{in} and T o ​ u ​ t T_{out} . Basically, the model can be described as

where embed \mathrm{embed} is the Input Embedding layer, multi − conv \mathrm{multi-conv} stands for our Multi-Kernel CNN, sconcat \mathrm{sconcat} is short for our SConcat module, transformer \mathrm{transformer} represents the transformer blocks and mlp \mathrm{mlp} contains a Linear layer and a Sigmoid function. Figure 5 shows the full picture of the model. You may find that the accessibility model is very similar to our DNA language model. Indeed, we only modify some of the model structures and change the hyperparameters, but they are all very critical adjustments which make the model suitable for the task.

embed \mathrm{embed} is the encoding layer transforming the input sequence into a feature matrix. The dimension conversion is ℕ L → ℝ L × E \mathbb{N}^{L}\xrightarrow{}\mathbb{R}^{L\times E} , Where L L is the length of the sequence and E E is the encoding length. Specifically, we encode the input as

Note that there is no segment − embed \mathrm{segment-embed} in this task because there is no need to distinguish different segments.

multi − conv \mathrm{multi-conv} has been explained in Section 3.1.2 . The dimension conversion is ℝ L × E → ℝ L × G \mathbb{R}^{L\times E}\xrightarrow{}\mathbb{R}^{L\times G} , where G G is the dimension of features learning from this layer.

sconcat \mathrm{sconcat} is the concat layer which fuses the features of the language model with the features learned from multi − conv \mathrm{multi-conv} . The dimension conversion is ℝ L × G → ℝ L × ( G + H ) \mathbb{R}^{L\times G}\xrightarrow{}\mathbb{R}^{L\times(G+H)} , where H H is the dimension of features generated from the DNA language model. Basically, we use the language model to construct features for sites in the sequence, and propose a smooth feature concat (SFC) method to fuse them with the previous features. What we do is

where T i ​ n ↔ \overleftrightarrow{T_{in}} stands for the context of sites in T i ​ n T_{in} , λ 1 \lambda_{1} and λ 2 \lambda_{2} are two network parameters with a dimension of ℝ L \mathbb{R}^{L} and LM \mathrm{LM} refers to our DNA language model. Here, it receives a DNA sequence, then constructs the context for each site in the sequence and produces an output of length H H . Specifically, if the length of the sequence is L L , it will construct L L pairs of context as the input and output a ℝ L × H \mathbb{R}^{L\times H} matrix.

Now we explain how we designed the smooth feature concat algorithm SFC. First, we have to mention that the output dimension of the language model is ℝ L × H \mathbb{R}^{L\times H} and the dimension of T c ​ n ​ n ​ s T_{cnns} is ℝ L × G \mathbb{R}^{L\times G} , which means we cannot directly apply SFA in this scenario.

Fortunately, the analysis in Section 3.1.2 has already given a solution. We can normalize the two distributions separately before concating them. However, this method uses LN \mathrm{LN} twice and consumes additional parameter space and data space. One doubt is that is it possible to use LN \mathrm{LN} only once? The answer is yes. Theorem 2 states that for any two distributions, there always exist two coefficients, so that the concat after they are multiplied by these two coefficients is a standardized distribution. That’s how our SFA works. We multiply the two tensors by two coefficients, and then do layer normalization after the concat of them. Thereby, we fuse the two features smoothly with only one LN \mathrm{LN} operation. Interestingly, this method is a weakened version of Theorem 2 .

transformer \mathrm{transformer} is the same as that described in Section 3.1.2 . The dimension conversion is ℝ L × F → ℝ L × F \mathbb{R}^{L\times F}\xrightarrow{}\mathbb{R}^{L\times F} where F = G + H F=G+H .

mlp \mathrm{mlp} is the output layer, responsible for transforming the hidden state to the output. The dimension conversion is ℝ L × F → ℕ \mathbb{R}^{L\times F}\xrightarrow{}\mathbb{N} . We extract the tensor corresponding to the token [ CLS ] \mathrm{[CLS]} , convert it into an output probability through a linear layer, and generate the prediction value via a sigmoid function. The output process is


## 4 Results and Discussions


## 4.1 SemanticDNA evaluation

no feature is SemanticCAP without pre-train features.

trans refers to transformer+linear.

mconv stands for our multi-conv layer.

PA is plain add, PC is plain concat and SFA is our smooth feature addition method.

trans is short for transformer blocks.

SFC is our smooth feature concat method.

We compared the performance of our proposed method with several baseline methods, including the gkmSVM ( Ghandi et al. 2014 ) , DeepSEA ( Zhou and Troyanskaya 2015 ) and kmer ( Min et al. 2017 ) . For the sake of fairness, all parameters were set as default. Besides, to prove the effectiveness of the DNA language model, we also tested our accessibility model excluding the DNA language model. For evaluation purpose, we computed two often-used measures, the area under the receiver operating characteristic curve (auROC) and the area under the precision-recall curve (auPRC), which are good indicators of the robustness of a prediction model. The classification results on six datasets are shown in Table 2 . Compared to the best baseline kmer, our system has a maximum 1.25 % 1.25\% improvement in auROC, and a maximum 2.41 % 2.41\% improvement in auPRC. Although some results on some datasets are not good, our model outperforms kmer on average, with 0.02 % 0.02\% higher auROC score and 0.1 % 0.1\% higher auPRC score. Compared to gkmSVM and DeepSEA, SemanticCAP has an about 2 % 2\% - 3 % 3\% improvement on average. Finally, the introduction of our DNA language model brings about a 2 % 2\% performance improvement.

We also tested the accessibility prediction accuracy of loci shared in different cell lines. For example, GM12878 and HeLa-S3 have 20 20 common loci, and the prediction accuracy of these 20 loci in both cell lines is 85 % 85\% and 90 % 90\% . Another example is that K562 and MCF-7 have 21 21 common loci, and the prediction accuracy is 80.9 % 80.9\% and 90.5 % 90.5\% , respectively. This shows the applicability of our system on the common loci between different cell lines.


## 4.2 Analysis of models

We did experiments on several different DNA language model structures, which can be roughly divided into two categories. The first category can be attributed to methods based on normal CNNs and the second uses our multi-conv architecture with data augmentation. Six structures are tested. At the same time, in order to test the prediction ability of different models in the case of insufficient information, we randomly masked some words and test the results. Complete results are shown in Table 3 . Through the comparison of LSTM and Attention, we can find that the attention mechanism can greatly improve the prediction ability of the DNA language model. When using the MaxPooling and ReLU functions, we observed that the output of the last hidden layer is mostly 0 0 , where the number of effective (not zero) neurons is about 3 / 256 3/256 . This is because the ReLU function shields neurons whose values are less than 0 0 , and MaxPooling selectively updates specific neurons. Therefore, we replace the MaxPooling with the AveragePooling, and the Attention layer that uses the ReLU function is replaced with a transformer. That’s the third method in Table 3 . The second category uses multi-conv to extract local features of the sequence. The introduction to multi-conv mechanism with data augmentation strategies brings increasement in accuracy, especially when we mask some tokens. There are three kinds of feature fusion strategies: plain concat (PC), plain add (PA) and our smooth feature add (SFA). The third, fourth, and fifth items in the table indicate that SFA outperforms the other two fusion methods. The last item in Table 3 , mconv(SFA)+trans, is the model we finally chose as our DNA language model.

We experimented with several chromatin accessibility model structures, which are all based on the transformer. The main difference is the use of multi-conv and the modules after the transformer. Complete comparison results are shown in Table 4 .

First focus on the module before the transformer. We notice that the introduction of multi-conv also brought performance improvements, especially in F1. In our chromatin accessibility model, we concat the features provided by the DNA language model, where we can either directly concat (PC) them or using our SFC method. The evaluation values of the last two items show the superiority of SFC.

Now turn to the comparison of modules after the transformer. The transformation from the features of transformer to the result is a challenge. In this part, five methods are tested. Mention that mconv+SFC+trans+linear is the final model. In terms of training time, our model can be fully parallelized, which is more advantageous than LSTM based on recurrent networks. At the same time, our model has fewer parameters and a simpler structure than Flatten after CNNs, thus can converge quickly. In terms of evaluation, LSTM-based methods perform poorly, and the main reason is that it is difficult for LSTM to learn the long-range dependence of a sequence. The convolution layer improves the performance of the LSTM to some extent by shortening the sequence length. In methods based on Flatten, the introduction of convolution layers actually reduces the accuracy. Maybe it’s because that the convolution layers destroy the sequence features learned from the transformer. During multiple chromatin accessibility models, the method using mult-conv and our smoother concat method SFC obtain the best results with relatively small number of parameters.


## 4.3 Analysis of [ CLS ] \mathrm{[CLS]}

We can observe the effectiveness of introducing the [ CLS ] \mathrm{[CLS]} symbol in our accessibility model. A direct indicator is the feature corresponding to [ CLS ] \mathrm{[CLS]} after the transformer layer, i.e., the value of T t ​ r ​ a ​ n ​ s [ ′ [ CLS ] ′ ] T_{trans}[^{\prime}\mathrm{[CLS]}^{\prime}] in Eq. 48 . We randomly selected a certain number of positive and negative samples and use our chromatin accessibility model to predict them. For each sample, we output the 256 256 -dimensional tensor corresponding to [ CLS ] \mathrm{[CLS]} after the transformer layer, and reduced it to two-dimensional space with t-SNE, which is shown in Figure 6 . According to it, the feature has an ability to distinguish positive and negative examples, which is strong evidence of its effectiveness.


## 4.4 Analysis of SFA \mathrm{SFA} and SFC \mathrm{SFC}

In this part we did two comparison experiments of PA, PC, SFA and SFC.

In the experiment of various DNA language models, we made a comparison between SFA, PA and PC, corresponding to the last three items in Table 3 . We used 5 × 10 6 5\times 10^{6} samples to train the three models, drew the training loss map of them and saw what would happen, which is shown in Figure 7 a. PA quickly reduces the loss at the fastest speed at the beginning, because all features in multi-conv are trained at the same time to the same degree. But in the later stage, there appears a phenomenon that some features are overtrained, while others are not, leading to the oscillation of loss.

In the experiment of various chromatin accessibility models, we made a comparison between SFC and PC, corresponding to the last two items in Table 4 . The first 5 × 10 3 5\times 10^{3} samples are used to measure its training state, which is shown in Figure 7 b. According to that, PC has a lower training speed, for it has a problem of gradient disappearance. Compared to it, the gradient propagation of SFA is selective and more stable for the whole term.

We can observe the effectiveness of SFA from another angle. Pay attention to the parameters C S ​ F ​ A C_{SFA} of SFA in multi-conv, whose dimension is ℝ K × L × H \mathbb{R}^{K\times L\times H} , where K K is the number of kernels, L L is the sequence length and H H is the hidden dimension. We normalized it and converted it to C S ​ F ​ A ′ C^{\prime}_{SFA} , whose dimension is ℝ K × L \mathbb{R}^{K\times L} . We do this for both the language model and the chromatin accessibility model, and picture them on Figure 8 . Note that the sum of the vertical axis is always 1 1 due to the normalization. Obviously, different sequence positions and different convolution kernels have different weights, which proves SFA’s ability to regulate features.

In general, SFA and SFC make training smoother, faster, and better. They are simple but effective. Actually, since they share the same essence (Hadamard product), they share the same advantages.


## 5 Conclusion

In this article, we propose a chromatin accessibility prediction model named SemanticCAP. Our model is able to predict open regions of DNA, thus having a guiding role in disease detection, drug design, etc. For example, a gene called CYMC from cell H1-hESC mutated in the middle with a length of 5 bp, and its accessibility decreased from 0.98 0.98 to 0.14 0.14 predicted by our model, which is consistent with the experimental data that it reduces transcription ( Klenova et al. 1993 ) . Another example is a mutation in a gene called HNF4A from cell K562, which leads to a reduction in gene expression ( Ellard and Colclough 2006 ) . Our model predicted that its accessibility decreased from 0.66 0.66 to 0.2 0.2 , which gives a reasonable explanation for the experimental phenomenon of reduction in gene expression caused by the mutation. Similarly, we can monitor the accessibility changes of DNA targeted by drugs (especially anticancer drugs), and the change of accessibility will provide guidance for drug action. The innovations of our method are as follows. First, we introduce the concept of language models in natural language processing to model DNA sequences. This method not only provides the word vector presentation of the base itself, but also provides sufficient information about the context of a site in a DNA sequence. Second, we use a small number of parameters to solve the feature fusion problem between different distributions. Specifically, we solve the problem of smooth addition of same dimensional distributions using SFA and the problem of smooth concat of different dimensional distributions using SFC. Third, we use an end-to-end model design, in which we fully utilize the learning ability and characteristics of the convolution and attention mechanism, thus achieving a better result with fewer parameters and shorter training time.

Of course, there is still much room for improvement in our method. In terms of the sample construction, we randomly select the same number of DNA sequences with the same length as negative samples. This approach may be modified. For example, we can deliberately use an unbalanced dataset, for there are so much DNA data, and then use some strategies such as ensemble learning ( Dietterich et al. 2002 ) to eliminate the negative effects of data imbalance ( Chawla and Sylvester 2007 ) . In terms of data input, sequence trucation or sequence completion operations exist in our model, which may cause information loss or redundant calculation. Also, the task we designed for the DNA language model could be enhanced. Multiple positions can be predicted simultaneously, just like the cloze problem in Bert. There are many other potential improvements. First is that the attention mechanism consumes too much memory, which could be replaced by a short-range attention or a mixed-length attention ( Choromanski et al. 2020 ) . Also, our smooth feature fusion method SFA and SFC could also be used in the multi-head attention to save space and accelerate training. Additionally, the dropout mechanism makes all neurons effective in the prediction phase, but there may exist a more reasonable way of fusing sub-networks. These issues need to be further explored.


## Acknowledgement

This work was supported by the following: the National Natural Science Foundation of China (31801108, 62002251); the Natural Science Foundation of Jiangsu Province Youth Fund (BK20200856); and A Project Funded by the Priority Academic Program Development of Jiangsu Higher Education Institutions (PAPD). This work was partially supported by the Collaborative Innovation Center of Novel Software Technology and Industrialization. The authors would also like to thank the support of Jiangsu Province Key Lab for providing information processing technologies.


## References