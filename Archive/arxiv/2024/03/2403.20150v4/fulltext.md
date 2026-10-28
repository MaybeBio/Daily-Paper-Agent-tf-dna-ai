## TFB: Towards Comprehensive and Fair Benchmarking of Time Series Forecasting Methods

Time series are generated in diverse domains such as economic, traffic, health, and energy, where forecasting of future values has numerous important applications. Not surprisingly, many forecasting methods are being proposed. To ensure progress, it is essential to be able to study and compare such methods empirically in a comprehensive and reliable manner. To achieve this, we propose TFB , an automated benchmark for Time Series Forecasting (TSF) methods. TFB advances the state-of-the-art by addressing shortcomings related to datasets, comparison methods, and evaluation pipelines: 1) insufficient coverage of data domains, 2) stereotype bias against traditional methods, and 3) inconsistent and inflexible pipelines. To achieve better domain coverage, we include datasets from 10 different domains : traffic, electricity, energy, the environment, nature, economic, stock markets, banking, health, and the web. We also provide a time series characterization to ensure that the selected datasets are comprehensive. To remove biases against some methods, we include a diverse range of methods, including statistical learning, machine learning, and deep learning methods, and we also support a variety of evaluation strategies and metrics to ensure a more comprehensive evaluations of different methods. To support the integration of different methods into the benchmark and enable fair comparisons, TFB features a flexible and scalable pipeline that eliminates biases. Next, we employ TFB to perform a thorough evaluation of 21 Univariate Time Series Forecasting (UTSF) methods on 8,068 univariate time series and 14 Multivariate Time Series Forecasting (MTSF) methods on 25 datasets. The results offer a deeper understanding of the forecasting methods, allowing us to better select the ones that are most suitable for particular datasets and settings. Overall, TFB and this evaluation provide researchers with improved means of designing new TSF methods.

PVLDB Reference Format: Xiangfei Qiu, Jilin Hu, Lekui Zhou, Xingjian Wu, Junyang Du, Buang Zhang, Chenjuan Guo, Aoying Zhou, Christian S. Jensen, Zhenli Sheng and Bin Yang. PVLDB, 17(9): 2363 - 2377, 2024. doi:10.14778/3665844.3665863

PVLDB Artifact Availability: The source code, data, and/or other artifacts have been made available at https://github.com/decisionintelligence/TFB .


## 1. Introduction

As part of the ongoing digitalization, time series are generated in a variety of domains, such as economic ( Sezer et al. 2020 ; Huang et al. 2022 ) , traffic ( Xu et al. 2023 ; Lin et al. 2023b ; Hu et al. 2018 ; Mo et al. 2022 ; Lin et al. 2024 ; Sun et al. 2023 ; Lin et al. 2021 ; Wan et al. 2022 ; Yang et al. 2023 ; Hu et al. 2019 ; Guo et al. 2020 ; Hu et al. 2017 ) , health ( Wei et al. 2022 ; Miao et al. 2021 ; Lee et al. 2017 ; Tran et al. 2019 ) , energy ( Alvarez et al. 2010 ; Guo et al. 2015 ) , and AIOps ( Campos et al. 2022 ; Wang et al. 2023 ; Qi et al. 2023 ; Campos et al. 2024 ; Kieu et al. 2022 ; Zhao et al. 2022 ) . Time Series Forecasting (TSF) is essential in key applications in these domains ( Pan et al. 2023 ; Guo et al. 2014 ; Yu et al. 2023 ; Yang et al. 2021 ) . Given historical observations, it is valuable if we can know the future values ahead of time. Correspondingly, TSF has been firmly established as an active research field, witnessing the proposal of numerous methods.

Time series organize data points chronologically and are either univariate or multivariate depending on the number of variables in each data point. Accordingly, TSF methods can be classified as either Univariate Time Series Forecasting (UTSF) or Multivariate Time Series Forecasting (MTSF) methods. Among early methods, Autoregressive Integrated Moving Average (ARIMA) ( Box and Pierce 1970 ) and Vector Autoregression (VAR) ( Toda and Phillips 1994 ) are arguably the most popular univariate and multivariate forecasting methods, respectively. Subsequent methods that exploit machine learning, e.g., XGBoost ( Chen and Guestrin 2016 ; Zhang et al. 2021 ) and Random Forest ( Breiman 2001 ; Mei et al. 2014 ) offer better performance than the early methods. Most recently, methods based on deep learning have demonstrated state-of-the-art (SOTA) forecasting performance on a variety of datasets ( Zhou et al. 2021 ; Nie et al. 2022 ; Wu et al. 2022 ; Zhang and Yan 2022 ; Chen et al. 2024 ; Yao et al. 2023 ; Wu et al. 2021b ; Wu et al. 2023 ; Zhao et al. 2023 ; Pedersen et al. 2020 ; Cheng et al. 2023 ; Cirstea et al. 2022b ; Cirstea et al. 2019 ; Cirstea et al. 2021 ; Lin et al. 2023a ; Miao et al. 2024 ) .

As more and more methods are being proposed for different datasets and settings, there is an increasing need for fair and comprehensive empirical evaluations. To achieve this, we identify and address three issues in existing evaluation frameworks, thereby advancing our evaluation capabilities.

Issue 1. Insufficient Coverage of Data Domains. Time series from different domains may exhibit diverse characteristics. Figure 1 a depicts a time series from the environment domain called AQShunyi ( Zhang et al. 2017 ) that records temperature information at hourly intervals, exhibiting a distinct seasonal pattern. This pattern is reasonable in this scenario because temperatures in nature often cycle around the year. Figure 1 b shows a time series from FRED-MD ( McCracken and Ng 2016 ) belongs to economic domain that describes the monthly macroeconomic from 114 regional, national, and international sources with a clear increasing tendency. This may be attributed to overall economic stability with minimal fluctuations, reflecting sustained growth in the macroeconomic indicators. Figure 1 c depicts a series among Electricity ( Trindade 2015 ) which comes from electricity domain and has a significant change in the data at a certain point in time, which might indicate an abrupt event, etc. However, these simple patterns are only the tip of the iceberg, and time series from different domains may exhibit much more complex patterns that either combine the above characteristics or are entirely different. Therefore, using only limited domains results in limited coverage of time series characteristics, which cannot offer a full picture.

However, few empirical studies and benchmarks cover a wide variety of data domains. Figure 2 summarizes the multivariate data domains used in existing forecasting benchmarks which include MTSF. We observe that TSlib ( Wu et al. 2022 ) , LTSF-Linear ( Zeng et al. 2023 ) , BasicTS ( Liang et al. 2022 ) , and BasicTS+ ( Shao et al. 2023 ) only include around 10 datasets, covering less than or equal to 5 domains. We observe that these datasets are concentrated in mainly two domains, namely traffic and electricity. Since the multivariate time series datasets in TSlib are the most used, we investigate the variations in the values of the characteristics of datasets in TSlib and TFB—see Figure 3 . We observe that the TFB datasets exhibit more diverse distributions than those of TSlib across the six characteristics. We argue that it is beneficial to broaden the coverage of domains, thereby enabling a more extensive assessment of method performance.

Issue 2. Stereotype bias against traditional methods. It is difficult for a single method to exhibit the best performance across all datasets. Methods exhibit varying performance across different datasets. To illustrate the issue, we conduct experiments on three datasets (NASDAQ ( Feng et al. 2019 ) , Wind ( Li et al. 2022 ) , and ILI ( Wu et al. 2021a ) ) from different domains (stock markets, energy, health) on methods VAR ( Toda and Phillips 1994 ) , PatchTST ( Nie et al. 2022 ) , LinearRegression (LR) ( Kedem and Fokianos 2005 ; Herzen et al. 2022 ) , NLinear ( Zeng et al. 2023 ) , FEDformer ( Zhou et al. 2022b ) , and Crossformer ( Zhang and Yan 2022 ) . Results are shown in Table 1 . Surprisingly, VAR outperforms all recently proposed SOTA methods on NASQAD and is better than FEDfomer and Crossformer on ILI. Furthermore, LR performs better than recently proposed SOTA methods on Wind. However, the experimental studies in their original papers ( Zhou et al. 2022b ; Zhang and Yan 2022 ; Nie et al. 2022 ) do not include VAR and LR in their baselines and rather assume that traditional methods are incapable of obtaining competitive performance. From Table 3 , it follows that no existing MTSF benchmark has evaluated statistical methods. Moreover, as the training mechanisms for statistical methods differ from those of deep learning-based methods, it is difficult for existing benchmarks to accommodate statistical methods. We argue that it is beneficial to eliminate stereotype bias against traditional methods by comparing a wide range of methods.

Issue 3. Lack of consistent and flexible pipelines. The performance of different methods varies with changing experimental settings, e.g., splits among training/validation/testing data, the choice of normalization method, and the selection of hyper-parameter settings. For example, implementations of existing methods often employ a “Drop Last” trick in the testing phase ( Zhou et al. 2022b ; Nie et al. 2022 ; Wang et al. 2022 ) . To accelerate the testing, it is common to split the data into batches. However, if we discard the last incomplete batch with fewer instances than the batch size, this causes unfair comparisons. For example, in Figure 4 , the ETTh2 ( Zhou et al. 2021 ) has a testing series of length 2,880, and we need to predict 336 future time steps using a look-back window of size 512. If we select the batch sizes to be 32, 64, and 128, the number of samples in the last batch are 17, 49, and 113, respectively. Discarding those last-batch testing samples is inappropriate unless all methods use the same strategy. Table 4 shows the testing results of PatchTST ( Nie et al. 2022 ) , DLinear ( Zeng et al. 2023 ) and FEDformer ( Zhou et al. 2022b ) on the ETTh2 with different batch sizes and the “Drop Last” trick turned on. We observe that the performance of the methods changes when varying the batch size. In addition, the pipelines in most benchmarks are inflexible and do not support simultaneous evaluation of statistical learning, machine learning, and deep learning methods. We argue that it is crucial to ensure a consistent and flexible pipeline so that methods are evaluated in the same setting, thereby improving the fairness of the findings.

Robust and extensive benchmarks enable researchers to evaluate proposals for new methods more rigorously across diverse range of datasets, which is crucial for advancing the state-of-the-art ( Tan et al. 2020 ; Qiao et al. 2024 ) . For example, ImageNet ( Deng et al. 2009 ) , that encompasses a substantial dataset has been instrumental in ensuring progress in computer vision. ImageNet has established itself as a standard for assessing methods in image processing due to its support for rigorous evaluation. Table 3 compares existing benchmarks for TSF according to seven properties. No existing benchmark possesses all properties.

We propose the Time series Forecasting Benchmark (TFB) to facilitate the empirical evaluation and comparison of TSF methods more comprehensively across application domains and methods, and with improved fairness. TFB contributes a collection of challenging and realistic datasets and provides a user-friendly, flexible, and scalable evaluation pipeline that offers robust evaluation support. TFB possesses the following key characteristics:

A comprehensive collection of datasets organized according to a taxonomy (to address Issue 1 ): Its collection of datasets offer diverse characteristics, encompassing time series from multiple domains and complex settings. This contributes to ensuring more robust and extensive evaluations.

Broad coverage of existing methods and extended support for evaluation strategies and metrics (to address Issue 2 ): TFB covers a diverse range of methods, including statistical learning, machine learning, and deep learning methods, accompanied by a variety of evaluation strategies and metrics. This richness enables more comprehensive evaluations across methods and evaluation settings.

Flexible and scalable pipeline (to address Issue 3 ): By its design, TFB improves the fairness of comparisons of methods. Methods are evaluated using a unified pipeline, consistent and standardized evaluation strategy and datasets are employed, eliminating biases and enabling more accurate performance comparisons. This enables more fair and meaningful conclusions regarding the effectiveness and efficiency of methods.

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

× \times

Based on the experiments conducted using TFB, we make the following key observations: (1) The statistical methods VAR ( Toda and Phillips 1994 ) and LinearRegression (LR) ( Kedem and Fokianos 2005 ; Herzen et al. 2022 ) perform better than recently proposed SOTA methods on some datasets—see Table 8 . (2) Linear-based methods perform well when datasets exhibit an increasing trend or significant shifts. (3) Transformer-based methods outperform linear-based methods on datasets with marked seasonality, and nonlinear patterns, as well as more pronounced patterns or strong internal similarities. (4) Methods that consider dependencies between channels can enhance the performance of MTSF substantially, particularly on datasets with strong correlations, compared to methods that assume channel independence.

We make the following main contributions.

We present TFB which is specifically designed to further improve fair comparisons in TSF, include UTSF and MTSF. TFB facilitates comparisons with 20+ UTSF methods on 8,068 univariate time series and 14 MTSF methods on 25 multivariate datasets.

We identify, collect, and process previously proposed TSF datasets to determine a comprehensive dataset covering diverse domains and characteristics and organize them in a standardized format. Then, we design experiments to study the performance of different methods over different characteristics of datasets.

TFB offers an automated end-to-end pipeline for evaluating forecasting methods, streamlining and standardizing the steps of loading time series datasets, configuring experiments, and evaluating methods. This simplifies the evaluation process for researchers. Additionally, all datasets and code are available at https://github.com/decisionintelligence/TFB .

We use TFB to evaluate and compare a diverse set of methods, covering statistical learning, machine learning, and deep learning methods and a rich array of evaluation tasks and strategies. We summarize the evaluation results into some key findings.

The rest of the paper is structured as follows. We review related work in Section 2 and introduce terms and definitions in Section 3 . In Section 4 , we cover the design of TFB, and in Section 5 , we use TFB to benchmark existing forecasting methods. We offer conclusions in Section 6 .


## 2. RELATED WORK

We proceed to first cover approaches to TSF and then review existing benchmarking proposals.

Time series forecasting: Existing methods for TSF can be categorized broadly into three main categories: statistical learning, machine learning, and deep learning methods.

Early proposals primarily employed statistical learning methods. ARIMA ( Box and Pierce 1970 ) , ETS ( Hyndman et al. 2008 ) , Theta ( Federico Garza 2022 ) , VAR ( Godahewa et al. 2021 ) , and Kalman Filter (KF) ( Harvey 1990 ) are classical and widely utilized methods. These forecasting methods are based on the idea that future values of time series can be predicted from observed, past values. With the rapid advances in machine learning technologies, machine learning methods for TSF have emerged ( Fischer et al. 2020 ) . Notably, XGBoost ( Chen and Guestrin 2016 ; Zhang et al. 2021 ) , Gradient Boosting Regression Trees (GBRT) ( Friedman 2001 ) , Random Forests ( Breiman 2001 ; Mei et al. 2014 ) and LightGBM ( Ke et al. 2017 ) have been applied extensively to better accommodate nonlinear relationships and complex patterns. Machine learning methods are flexibile at handling different types and lengths of time series and generally offer better forecasting accuracy than traditional methods.

However, these methods still require manual feature engineering and model design. Taking advantage of the representation learning capabilities offered by deep neural networks (DNNs) on rich data, numerous deep learning methods have been proposed. In many cases, these methods outperform traditional techniques in terms of forecasting accuracy. TCN ( Bai et al. 2018 ) and DeepAR ( Salinas et al. 2020 ) treat time series as sequences of vectors and utilize CNNs or RNNs to capture temporal dependencies. Additionally, Transformer architectures, including Informer ( Zhou et al. 2021 ) , FEDformer ( Zhou et al. 2022b ) , Autoformer ( Wu et al. 2021a ) , Triformer ( Cirstea et al. 2022a ) , and PatchTST ( Nie et al. 2022 ) can capture more complex temporal dynamics, significantly improving forecasting performance. MLP-based models such as N-HiTS ( Challu et al. 2023 ) , N-BEATS ( Oreshkin et al. 2019 ) , NLinear ( Zeng et al. 2023 ) , and DLinear ( Zeng et al. 2023 ) employ a simple architecture with relatively few parameters and have also demonstrated good forecasting accuracy.

Benchmarks: Several benchmarks for TSF have been proposed: Libra ( Bauer et al. 2021 ) , BasicTS ( Liang et al. 2022 ) , BasicTS+ ( Shao et al. 2023 ) , Monash ( Godahewa et al. 2021 ) , M3 ( Makridakis and Hibon 2000 ) , M4 ( Makridakis et al. 2018 ) , LTSF-Linear ( Zeng et al. 2023 ) and TSlib ( Wu et al. 2022 ) . However, these benchmarks fall short in different aspects—see Table 3 .

First, most benchmarks consider either univariate or multivariate time series forecasting. Early works, i.e., M3 ( Makridakis and Hibon 2000 ) , M4 ( Makridakis et al. 2018 ) , Libra ( Bauer et al. 2021 ) and Monash ( Godahewa et al. 2021 ) , only pay attention to univariate time series. And recent works, e.g., LTSF-Linear ( Zeng et al. 2023 ) , BasicTS ( Liang et al. 2022 ) and BasicTS+ ( Shao et al. 2023 ) , just consider multivariate. Only TSlib ( Wu et al. 2022 ) considers both.

Second, a notable issue arises regarding the assessment of method diversity. In the early times, the deep learning methods are not dominant in TSF, so most early benchmarks do not have deep learning methods in their comparison, e.g., M3 ( Makridakis and Hibon 2000 ) , M4 ( Makridakis et al. 2018 ) and Libra ( Bauer et al. 2021 ) . On the contrary, with more deep learning methods demonstrating their performance in TSF, recent benchmarks focus solely on deep learning methods, e.g., LTSF-Linear ( Zeng et al. 2023 ) , TSlib ( Wu et al. 2022 ) , BasicTS ( Liang et al. 2022 ) and BasicTS+ ( Shao et al. 2023 ) . As mentioned in Section 1 , this limited coverage of different method paradigms is a concern.

Moreover, there is a challenge regarding scalable and unified pipelines. In the earliest works, M3 ( Makridakis and Hibon 2000 ) and M4 ( Makridakis et al. 2018 ) do not provide a pipeline in their benchmark at all, making it hard to integrate new methods. Monash ( Godahewa et al. 2021 ) and Libra ( Bauer et al. 2021 ) have pipelines but it is designed for statistical methods, which are unable to integrate deep learning methods. On the contrary, LTSF-Linear ( Zeng et al. 2023 ) and TSlib ( Wu et al. 2022 ) have pipelines specific to deep learning methods, which are unable to evaluate statistical methods. We consider these pipelines to be incomplete, reducing scalability and hindering their broader application of these benchmarks.

Furthermore, the majority of benchmarks do not categorize the dataset; only BasicTS+ ( Shao et al. 2023 ) provides a coarse-grained classification. We consider this taxonomy to be incomplete. In contrast, TFB involves a fine-grained classification of the dataset.

Generally, TFB aims to enable a more reliable, thorough, and user-friendly evaluation. Thus, the proposed benchmark encompasses a broader range of methods and utilizes more scalable implementation pipelines than existing benchmarks, ensuring a fair comparison of TSF methods and promoting progress in the field of TSF.


## 3. Preliminaries

We provide definitions of time series and time series forecasting, and we cover key dataset characteristics, including trend, seasonality, stationarity, shifting, transition, and correlation.

A time series X ∈ ℝ T × N X\in\mathbb{R}^{T\times N} is a time-oriented sequence of N-dimensional time points, where T T is the number of time points, and N N is the number of variables. When N = 1 N=1 , a time series is called univariate. When N > 1 N>1 , it is called multivariate.

Given a historical time series X ∈ ℝ H × N X\in\mathbb{R}^{H\times N} of H H time points, time series forecasting aims to predict the next F F future time points, i.e., Y ∈ ℝ F × N Y\in\mathbb{R}^{F\times N} , where F F is called the forecasting horizon.

The trend of a time series refers to the long-term changes or patterns that occur over time. Intuitively, it represents the general direction in which the data is moving. Referring to the explained variance ( O’Grady 1982 ) , Trend Strength can be defined as follows.

where X X is a time series that can be decomposed into a trend ( T ) (T) , seasonality ( S ) (S) , and the remainder ( R ) (R) : X = S + T + R X=S+T+R by employing Seasonal and Trend decomposition using Loess, which is a highly versatile and robust method for time series decomposition ( Cleveland et al. 1990 ) .

Input: Time series X ∈ ℝ T × 1 X\in\mathbb{R}^{T\times 1}

Output: Shifting value δ \delta ∈ ( 0 , 1 ) \in(0,1) of X X

Input: Time series X ∈ ℝ T × 1 X\in\mathbb{R}^{T\times 1}

Output: Transition value Δ \Delta ∈ ( 0 , 1 3 ) \in(0,\frac{1}{3}) of X X

Seasonality refers to the phenomenon where changes in a time series repeat at specific intervals. Similar to the measurement of trend, the strength of Seasonality of a time series X X can be estimated as follows.

Stationarity refers to the mean of any observation in a time series X = ⟨ x 1 , x 2 , … , x n ⟩ X=\langle x_{1},x_{2},...,x_{n}\rangle is constant, and the variance is finite for all observations. Also, the covariance 𝑐𝑜𝑣 ⁡ ( x i , x j ) \mathit{cov}(x_{i},x_{j}) between any two observations x i x_{i} and x j x_{j} depends only on their distance | j − i | |j-i| , i.e., ∀ i + r ≤ n , j + r ≤ n \forall i+r\leq n,j+r\leq n ( 𝑐𝑜𝑣 ⁡ ( x i , x j ) = 𝑐𝑜𝑣 ⁡ ( x i + r , x j + r ) ) . (\mathit{cov}(x_{i},x_{j})=\mathit{cov}(x_{i+r},x_{j+r})). Strictly stationary time series are rare in practice. Therefore, weak stationarity conditions are commonly applied ( Lee 2017 ) ( Nason 2006 ) . In our paper, we also exclusively focus on weak stationarity.

We adopt the Augmented Dick-Fuller (ADF) test statistic ( Elliott et al. 1992 ) to quntify stationarity. The stationarity can be calculated as follows.

Shifting refers to the phenomenon where the probability distribution of time series changes over time. This behavior can stem from structural changes within the system, external influences, or the occurrence of random events. As the value approaches 1, the degree of shifting becomes more severe. Algorithm 1 details the calculation process.

Transition refers to the trace of the covariance of transition matrix between symbols in a 3-letter alphabet ( Lubba et al. 2019 ) . It captures the regular and identifiable fixed features present in a time series, such as the clear manifestation of trends, periodicity, or the simultaneous presence of both seasonality and trend. Algorithm 2 details the calculation process.

Correlation refers to the possibility that different variables in a multivariate time series may share common trends or patterns, indicating that they are influenced by similar factors or have some underlying relationship. Correlation is calculated as follows.

First, use Catch22 ( Lubba et al. 2019 ) to extract 22 features for each variable in X X , serving as a representation for each variable. F = ⟨ F 1 , F 2 , … , F N ⟩ ∈ ℝ 22 × N F=\langle F^{1},F^{2},...,F^{N}\rangle\in\mathbb{R}^{22\times N} is obtained using the formulation specified in Equation 4 .

Second, according to Equation 5 we calculate the Pearson correlation coefficient between all variable pairs.

Third, compute the mean and variance of all Pearson correlation coefficients (PCCs) ( Cohen et al. 2009 ) to obtain the correlation, as shown in Equation 6 .

Figure 1 shows time series exhibit diverse characteristics in real-world scenarios. For each characteristic, the calculated characteristic values in the upper right corner of the image corresponding to series with distinct and indistinct characteristic are significantly different. In summary, the time series characteristics define here enable a deep understanding of time series. Using these characteristics for classifying time series, we can more selectively choose forecasting methods that are appropriate for specific scenarios.


## 4. TFB: BENCHMARK DETAILS

We proceed to cover the design of the TFB benchmark. First, we provide a detailed overview of the dataset in TFB, including the process of collection, accompanied by a comprehensive demonstration. (Section 4.1 ). Second, we categorize the existing methods supported (Section 4.2 ). Third, we cover evaluation strategies and metrics (Section 4.3 ). Finally, we describe the full benchmark pipeline (Section 4.4 ).

| T ​ S | < 300 |TS|\textless 300 : the length of univariate time series <300

F F : the forecasting horizon


## 4.1. Datasets

We equip TFB with a set of 25 multivariate and 8,068 univariate datasets with the following desirable properties. All datasets are formatted consistently. The collection is comprehensive, covering a wide range of domains and characteristics. The values of key characteristics of the multivariate and univariate datasets, as well as their classification based on the characteristics, can be found in our code repository. This marks an improvement, addressing challenges such as different formats, varied documentation, and the time-consuming nature of dataset collection. We will provide a brief introduction to these datasets (Section 4.1.1 ), demonstrating their comprehensiveness (Section 4.1.2 ).

Univariate time series. The univariate datasets are carefully curated from 16 open-source datasets, thus covering dozens of domains. To fully reflect the complexity of real-world time series, we employed Principal Feature Analysis (PFA) ( Lu et al. 2007 ) , a variation of Principal Component Analysis (PCA) ( Bro and Smilde 2014 ) . PFA preserves the original values of individual time series data points. We employ the concept of explained variance, representing the ratio between the variance of a single time series and the sum of variances across all individual time series. A threshold t t for the explained variance is set to 0.9. This implies that for each dataset, we choose to retain the minimum number of time series required to encompass 90% of the variance contributed by the remaining time series. As a result, the selected data exhibits pronounced heterogeneity. Compared to datasets with strong homogeneity, it can better reflect methods performance. In the end, we select 8,068 time series to enable the combined dataset to capture the diversity of real-world time series. Statistical information is reported in Table 4 .

Multivariate time series. Table 5 lists statistics of the 25 multivariate time series datasets, which cover 10 domains. The frequencies vary from 5 minutes to 1 month, the range of feature dimensions varies from 5 to 2,000, and the sequence length varies from 728 to 57,600. This substantial diversity of the datasets enables comprehensive studies of forecasting methods. To ensure fair comparisons, we choose a fixed data split ratio for each dataset chronologically, i.e., 7:1:2 or 6:2:2, for training, validation and testing.

We proceed to investigate the coverage of the selected univariate and multivariate datasets.

Univariate time series. Since time series have different lengths, we first represent time series as vectors that consist of five feature indicators: trend, seasonality, stationarity, shifting, and transition. For ease of visualization, we adopt PCA ( Bro and Smilde 2014 ) to reduce the dimensionality from five to two and visualize the eight most widely distributed univariate time series datasets in hexbin—see Figure 5 . We observe that TFB and M4 cover the most cells, while all other benchmarks are smaller than TFB. This emphasizes the coverage of our dataset in terms of diversity in characteristic distribution. In addition, compared to M4, our dataset covers a wider range of domains. Further, we note that M4 has a much larger sample size, totaling 100,000, compared to our dataset that contains only 8,068 time series. We believe that testing on diverse datasets is essential to better reflect the practical performance of methods. Yet, we can run much fewer experiments with TFB than the M4 dataset, i.e., around 8%.

Multivariate time series. Figure 2 shows a comparison of TFB and existing multivariate time series benchmarks according to dataset domain distribution. Our benchmark includes more diverse datasets in terms of both quantity and domain categories. Next, we select TSlib, whose multivariate time series datasets are the most popular, to compare the characteristic distributions with TFB, which are shown in Figure 3 . We can observe that the datasets in TFB also represent a more diverse characteristic distribution.


## 4.2. Comparison Methods

To investigate the strengths and limitations of different forecasting methods, we include 22 methods that can be categorized as statistical learning, machine learning, and deep learning methods. In terms of statistical learning methods, we include ARIMA ( Box and Pierce 1970 ) , ETS ( Hyndman et al. 2008 ) , Kalman Filter (KF) ( Harvey 1990 ) , and VAR ( Toda and Phillips 1994 ) . Among the machine learning methods, we include XGBModel (XGB) ( Herzen et al. 2022 ) , LinearRegression (LR) ( Kedem and Fokianos 2005 ; Herzen et al. 2022 ) , and Random Forest (RF) ( Breiman 2001 ) . Finally, we further split the deep learning methods into RNN-based models (RNN ( Kim et al. 2021 ) ), CNN-based models (MICN ( Wang et al. 2022 ) , TimesNet ( Wu et al. 2022 ) , and TCN ( Bai et al. 2018 ) ), MLP-based models (NLinear ( Zeng et al. 2023 ) , DLinear ( Zeng et al. 2023 ) , TiDE ( Das et al. 2023 ) , N-HiTS ( Challu et al. 2023 ) , and N-BEATS ( Oreshkin et al. 2019 ) ), Transformer-based models (PatchTST ( Nie et al. 2022 ) , Crossformer ( Zhang and Yan 2022 ) , and FEDformer ( Zhou et al. 2022b ) , Non-stationary Transformer (Stationary) ( Liu et al. 2022 ) , Informer ( Zhou et al. 2021 ) , and Triformer ( Cirstea et al. 2022a ) ), and Model-Agnostic models (FiLM ( Zhou et al. 2022a ) ).


## 4.3. Evaluation Settings

To assess the forecasting accuracy of a method, TFB implements two distinct evaluation strategies: 1) Fixed forecasting; and 2) Rolling forecasting .

Fixed forecasting. Given a time series on length n n , f f future time points are predicted from n − f n-f historical time points, which is illustrated in Figure 6(a) .

Rolling forecasting. In Rolling forecasting, illustrated in Figure 6(b) , the blue squares represent historical data, the green squares represent the forecasting horizon, and the white squares represent the remaining data in the time series. During rolling forecast, excluding the last iteration, the historical data expands by a fixed number of steps (called the stride) in each iteration. In the final iteration, the historical data is extended to cover the entire time series along with the forecasting horizon. In each iteration of the inference process, the forecasting model is applied based on the historical data to forecast the designated forecasting horizon. Then, we calculate the average of the error metrics for each iteration. In statistical learning methods (e.g., ARIMA ( Box and Pierce 1970 ) , ETS ( Federico Garza 2022 ) ), it is common to use the entire or a subset of the historical data for training and then make forecasting during each iteration. In contrast, in deep learning or machine learning methods, each iteration often involves using only the last portion of the historical data, with a length equal to the look-back windows size, for inference to make forecasting. The current evaluation strategy for TSF, such as TimesNet ( Wu et al. 2022 ) , aligns with our defined criteria.

From a practical perspective, despite some limitations in the generalization capabilities of statistical learning methods, their relatively short runtimes prompts us to adopt the approach of retraining and then making inference predictions to support rolling forecasting. However, in the case of deep learning and machine learning methods, each iteration of retraining typically takes much longer time. Therefore, to balance timeliness and prediction accuracy, machine learning and deep learning methods opt for the strategy of reinferring during each iteration in rolling forecasting.

To achieve an extensive evaluation of forecasting performance, we employ eight error metrics, namely the Mean Absolute Error (MAE), Mean Absolute Percentage Error (MAPE), Mean Squared Error (MSE), Symmetric Mean Absolute Percentage Error (SMAPE), Root Mean Squared Error (RMSE), Weighted Absolute Percent Error (WAPE), Modified Symmetric Mean Absolute Percentage Error (MSMAPE) ( Suilin 2017 ) , and Mean Absolute Scaled Error (MASE) ( Hyndman and Koehler 2006 ) , which are defined in Equations 7 – 14 .

where M M is the length of the training series, S S is the seasonality of the dataset, h h is the forecasting horizon, F k F_{k} are the generated forecasts , and Y k Y_{k} are the actual values. We set the parameter ϵ \epsilon in Equation 13 to its proposed default of 0.1. For rolling forecasting, we further calculate the average of error metrics for all samples (windows) on each time series to assess the method performance.


## 4.4. Unified Pipeline

As mentioned in Section 1 , small implementation differences can impact evaluation results profoundly. To enable fair and comprehensive comparisons of methods, we introduce a unified pipeline that is structured into a data layer, a method layer, an evaluation layer, and a reporting layer—see Figure 7 . The details of each component are listed as follows.

The data layer is a repository of univariate and multivariate time series from diverse domains, structured according to their distinct characteristics, frequencies, and sequence lengths. The data is uniformly according to a standardized format. When a new dataset becomes available, this layer can assess whether the distribution of existing datasets across the six features can be expanded. If yes, it is accepted as a new dataset.

The method layer supports embedding statistical learning, machine learning and deep learning methods. However, other benchmarks have not achieved this, most of them can only embed deep learning methods. Additionally, TFB is designed to be compatible with any third-party TSF library, such as Darts ( Herzen et al. 2022 ) , TSlib ( Wu et al. 2022 ) . Users can easily integrate forecasting methods implemented in third-party libraries into TFB by writing a simple Universal Interface, facilitating fair comparisons. TFB goes beyond benchmarks that only support Direct Multi-Step (DMS) forecasting to support also Iterative Multi-Step (IMS) forecasting. The method layer thus contributes to the applicability of TFB by offering support for a broad range of methods.

The evaluation layer offers support for a diverse range of evaluation strategies and metrics. It thus supports both fixed and rolling forecasting strategies, increasing again the applicability of the benchmark to a wider range of methods and applications. The layer also covers evaluation metrics found in other studies and enables the use of customized metrics for a more comprehensive assessment of method performance. Besides, for each evaluation strategy, TFB offers standardized dataset handling, splitting, and normalization. Additionally, it provides a standard configuration file that can be customized by users. This aims to facilitate deeper understanding of method performance in different settings.

The reporting layer encompasses a logging system for tracking information, enabling the capture of experimental settings to enable traceability. Further, it encompasses a visualization module to facilitate a clear understanding of method performance. This design is to offer exhaustive support and transparency throughout the evaluation process.

Users only need to deploy their method architecture at the method layer and choose or configure the configuration file, then TFB can automatically run the pipeline in Figure 7 .

The TFB pipeline supports various extensible features. Compatibility with CPU and GPU hardware enables evaluation in different computing environments. TFB also supports both sequential and parallel program execution, providing users with multiple options.

In summary, TFB is a unified, flexible, scalable, and user-friendly benchmarking tool for TSF methods. It enables to better understand, compare, and select TSF methods for specific application scenarios.


## 5. EXPERIMENTS

We report on experiments with the 14 multivariate and 22 univariate forecasting methods covered in Section 4.2 on all the datasets covered in Section 4.1 . We adopt the pipeline covered in Section 4.4 to do so. For each method, we conduct comprehensive hyper-parameters selection, such that its performance result approach or surpass the performance reported in its original paper. Our goal is to showcase TFB as an easy-to-use and powerful resource, providing a convenient and fair evaluation platform for TSF methods.


## 5.1. Experimental Setup

We include all the datasets included in TFB and all methods mentioned in Section 4.2 .

For multivariate forecasting, we use the rolling forecasting strategy. We consider four forecasting horizon F F : 24, 36, 48, and 60, for FredMd, NASDAQ, NYSE, NN5, ILI, Covid-19, and Wike2000, and we use another four forecasting horizon, 96, 192, 336, and 720, for all other datasets which have longer lengths. The look-back window H H underwent testing with lengths 36 and 104 for FredMd, NASDAQ, NYSE, NN5, ILI, Covid-19, and Wike2000, and 96, 336, and 512 for all other datasets. For univariate forecasting, we adopt a fixed forecasting strategy to maintain consistency with the setting of the M4 competition ( Makridakis et al. 2018 ) , forecasting horizons go from 6 to 48, with the look-back window H H set to 1.25 times forecasting horizon F F .

For each method, we adhere to the hyper-parameter as specified in their original papers. Additionally, we perform hyper-parameter searches across multiple sets, with a limit of 8 sets. The optimal result is then selected from these evaluations, contributing to a comprehensive and unbiased assessment of each method’s performance. Due to space constraints, we only report the results of a subset of metrics in the paper, additional metrics results can be found in the code repository.

All experiments are conducted using PyTorch ( Paszke et al. 2019 ) in Python 3.8 and execute on an NVIDIA Tesla-A800 GPU. The training process is guided by the L2 loss, employing the ADAM optimizer. Initially, the batch size is set to 32, with the option to reduce it by half (to a minimum of 8) in case of an Out-Of-Memory (OOM) situation. We do not use the "Drop Last" operation during testing. To ensure reproducibility and facilitate experimentation, datasets and code are available at: https://github.com/decisionintelligence/TFB .


## 5.2. Experimental Results

Table 6 reports the average results of UTSF in terms of the metrics MASE, MSMAPE, and the Ranks in MSMAPE that indicates how many times the best performance is achieved on the datasets. We observe that the recently proposed deep learning methods, including TimesNet ( Wu et al. 2022 ) , PatchTST ( Nie et al. 2022 ) , and N-HiTS ( Challu et al. 2023 ) , exhibit substantially better average performance on univariate datasets in terms of MASE and MSMAPE. However, when considering Ranks, the (non-deep) machine learning methods LinearRegression (LR) ( Kedem and Fokianos 2005 ; Herzen et al. 2022 ) and RandomForest (RF) ( Breiman 2001 ) outperform all competitors. This suggests that the machine learning methods may be more suitable in specific scenarios. In this scenario, each individual univariate time series is adopted to train a separate model, and deep learning methods require large amount of training data to be effective. Therefore, the performance of the deep learning methods falls short. Next, we can observe that LR performs better on the time series with seasonality, trend, and shifting characteristics, while RF is better when those patterns are absent. Further, we notice that LR is more suitable for data without stationarity than RF. Finally, both LR and RF are sensitive to the transition characteristic: the stronger the characteristic, the better. These results offer guidance on choosing the right method for a specific setting.

Due to the large number of results, we report them in two tables, Tables 7 and 8 . The datasets in these tables are ordered based on their trend characteristic, where datasets with weaker trend are occur first. In both tables, we report the MAE and MSE on normalized data considering four different forecasting horizons for each dataset. "nan" represents the inability of a method to generate effective predictions, while "inf" represents infinite results. We see that no single method achieves the best performance on all datasets. We also see that the Transformer-based methods generally outperform other methods on datasets with weak trend. Next, Linear-based methods tend to perform moderately better on datasets with strong trend. Surprisingly, we observe that recent methods not consistently outperform earlier studies, such as Informer, LR, and VAR. This discovery highlights the need for evaluating method performance across diverse datasets. Evaluating methods on relatively few datasets render it difficult to accurately assess their universality and overall performance. Therefore, it is crucial to expand the range of datasets used in evaluations.

We proceed to study the performance of different deep learning methods with respect to different characteristics. First, we score the multivariate time series with respect to the six characteristics we consider. Then, we select the dataset with the highest score for each characteristic, which are FRED-MD on trend, Electricity on seasonality, PEMS08 on transition, NYSE on shifting, PEMS-BAY on correlation, and Solar on stationarity. Next, we show the best MAE results for the methods in a radar figure. We use a forecasting horizon of 24 for FRED-MD and NYSE and of 96 for other datasets—see Figure 8 . We see that no deep learning method excels on all datasets. In particular, Crossformer demonstrates exceptional performance on datasets where transition is highly pronounced (PEMS08), the data is most stationary (Solar), and the data is most correlated (PEMS-BAY). However, Crossformer’s performance is noticeably inferior to other methods on time series with other characteristics. Next, PatchTST achieves optimal performance on datasets with strong seasonality (Electricity). Similarly, NLinear delivers outstanding results on time series with the most significant trend (FRED-MD) and severe drift (NYSE). Both PatchTST and NLinear perform well consistently, without any notably poor outcomes.


## 5.3. Hints to Method Design

To study the impact of different data characteristics on these two types of methods, we consider the best MAE results obtained by CNN, Linear and Transformer. We use a forecasting horizon of 24 for NASDAQ, NYSE, and NN5 and of 96 for other datasets—see Figure 9 . We choose CNN as a reference to gain a more comprehensive understanding of the performance of Transformer and Linear methods. We have the following observations. First, each method exhibits distinct advantages on datasets with different characteristics. Second, Linear-based methods excel when the dataset shows an increasing trend or significant shifts. This can be attributed to the linear modeling capabilities of the Linear model, making it well-suited for capturing linear trends and shifts. Third, Transformer-based methods outperform Linear-based methods on datasets exhibiting marked seasonality, stationarity, and nonlinear patterns, as well as more pronounced patterns or strong internal similarities. This superiority may stem from the enhanced nonlinear modeling capabilities of Transformer-based methods, enabling them to flexibly adapt to complex time series patterns and intrinsic correlations.

Therefore, the observed phenomenon underscores the inherent differences between Transformer-based and Linear-based methods at addressing diverse characteristics of time series. To achieve optimal performance, we recommend selecting the appropriate method based on the characteristics of the relevant time series, allowing the method to fully leverage its strengths.

In multivariate datasets, variables are occasionally referred to as channels. To study the impact of channel dependency in multivariate time series, we compare PatchTST and Crossformer on ten datasets with dependencies ranging from weak to strong. We report the MAE for forecasting horizon F F is 96 in Figure 10 . We observe that as the correlations within a dataset increase, the performance of Crossformer gradually surpasses that of PatchTST, suggesting that it is better to consider channel dependencies when correlations are strong. However, when correlations among variables are not pronounced, PatchTST that does not consider channel dependencies is better.

This observation indicates that introducing consideration for dependencies between channels can significantly improve the performance of multivariate time series prediction, especially on datasets with strong correlations, when compared to methods that assume channel independence. This suggests that when designing new forecasting methods, attention should be given to leveraging and fully utilizing the relationships between variables, thereby capturing more accurately the underlying structures and patterns in the dataset. However, when the correlation within a dataset is not pronounced, the performance of the Crossformer method, considering channel dependencies, may not outperform PatchTST. Therefore, it is of interest to find better ways to effectively leverage channel dependencies. This in-depth exploration and balancing of channel dependencies provides guidance for the design of new methods and the performance optimization of existing ones.

We study the performance of deep learning methods in MTSF about inference time and parameter counts. Due to space constraints, we choose three datasets with different scales, namely Traffic (large), Weather (medium), and ILI (small). We use the forecasting horizon of 24 for ILI, while it is 96 for Traffic and Weather. The results are shown in Figure 11 , where the horizontal axis represents the number of parameters on a logarithmic scale and the vertical axis represents the inference time per sample (window in the test dataset) in milliseconds, which is also on a logarithmic scale. The reported parameter counts and inference times refer to the method’s best performance on the dataset. We observe a general upward trend in the inference time as the number of parameters increases, which is intuitive. When considering the running time and number of parameters, Linear-based methods outperform CNN-based and Transformer-based methods. Further, CNN-based methods tend to have a larger number of parameters. Among the Transformer-based methods, we can also observe that PatchTST demonstrates a notable advantage over Triformer and Crossformer in terms of running time.


## 6. Conclusions

We present the TFB time series forecasting benchmark that addresses three issues to enable comprehensive and reliable comparison of TSF methods. To alleviate the insufficient data domains problem , TFB includes datasets from a total of 10 different domains, covering traffic, electricity, energy, environment, nature, economics, stock, banking, health, and web. We also include a time series characteristics analysis to ensure that selected datasets are well distributed across different characteristics. To remove the bias on traditional methods, TFB covers a diverse range of methods, including statistical learning, machine learning, and deep learning methods, accompanied by a variety of evaluation strategies and metrics. Thus, TFB can evaluate the performance of different methods comprehensively. To address the inconsistent and inflexible pipelines problem, TFB offers a new flexible and scalable pipeline, eliminating biases and providing a better basis for performance comparison. Overall, TFB is a more comprehensive and fair benchmark that aims to promote the development of new TSF methods.


## References