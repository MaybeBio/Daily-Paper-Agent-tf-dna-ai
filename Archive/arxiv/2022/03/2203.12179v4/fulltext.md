## Targeted Function Balancing Thanks: We thank Chad Hazlett for advising us throughout the course of this project. We also thank Kenai Burton-Heckman for leading the development of the R Package tfb , which implements the method proposed here. We also thank Erin Hartman, Onyebuchi Arah, Mark Handcock, Avi Feller, Yixin Wang, the UCLA Practical Causal Inference Lab, and anonymous reviewers for their valuable comments and suggestions.

This paper introduces Targeted Function Balancing (TFB), a covariate balancing weights framework for estimating the average treatment effect of a binary intervention. TFB first regresses an outcome on covariates, and then selects weights that balance functions (of the covariates) that are probabilistically near the resulting regression function. This yields balance in the regression function’s predicted values and the covariates, with the regression function’s estimated variance determining how much balance in the covariates is sufficient. Notably, TFB demonstrates that intentionally leaving imbalance in some covariates can increase efficiency without introducing bias, challenging traditions that warn against imbalance in any variable. Additionally, TFB is entirely defined by a regression function and its estimated variance, turning the problem of how best to balance the covariates into how best to model the outcome. Kernel regularized least squares (KRLS), the LASSO, and Bayesian Additive Regression Trees (BART) are considered as regression estimators. With KRLS, TFB contributes to the literature of kernel-based weights. As for the LASSO, TFB uses the regression function’s estimated variance to prioritize balance in certain dimensions of the covariates, a feature that can be greatly exploited by choosing a sparse regression estimator. With BART, we demonstrate that TFB can apply regression estimators that do not have linear representations. The R Package tfb implements TFB.

Keywords: Augmented estimator, average treatment effect, balancing weight, causal inference, kernel, propensity score


## 1 Introduction

Weighting is commonly employed to estimate the causal effect of an intervention, D i D_{i} , on an outcome of interest, Y i Y_{i} . When the average treatment effect on the treated is the target estimand, and given covariates, X i X_{i} , that make up all confounders, investigators seek weights that render the control (i.e., untreated) group more similar to the treated group on X i X_{i} . Weights based on the probability of being treated given X i X_{i} , π ⁡ ( X i ) \pi(X_{i}) or the propensity score ( Rosenbaum and Rubin, 1983 ), equate the distribution of X i X_{i} in the control group to that in the treated group in expectation, and yield a weighted difference in means, τ ^ wdim \hat{\tau}_{\mathrm{wdim}} , that is unbiased. But these weights require π \pi to be known or consistently estimated, which is unrealistic, and misspecifying π \pi can bring large biases (e.g., Kang and Schafer, 2007 ). Another approach is to find weights that make the means of X i X_{i} more similar between the groups, referred to here as “balancing”, or seeking “balance” in, X i X_{i} . This can be easily extended to weights that instead, or additionally, balance a transformation of X i X_{i} (e.g., its squares and pair-wise interactions) by replacing X i X_{i} with, or adding to it, said transformation.

One family of balancing methods includes those that equate the means of X i X_{i} in both groups, or balance X i X_{i} “exactly” (e.g., Hainmueller, 2012 ; Chan et al., 2016 ). However, these methods have two limitations — one of feasibility, and one of specification. On feasibility, such weights may not exist (e.g., when X i X_{i} is of large dimension) or have high variance, resulting in a high variance τ ^ wdim \hat{\tau}_{\mathrm{wdim}} . On specification, such weights only guarantee an unbiased τ ^ wdim \hat{\tau}_{\mathrm{wdim}} when the conditional expectation function of Y i Y_{i} given X i X_{i} and without treatment, f 0 ​ ( X i ) = 𝔼 ⁡ ( Y i | D i = 0 , X i ) f_{0}(X_{i})=\mathbbm{E}(Y_{i}\ |\ D_{i}=0,X_{i}) , is linear in X i X_{i} . Further, these limitations compound each other — exactly balancing a high-dimensional transformation of X i X_{i} (e.g., high-degree polynomial terms) would yield an unbiased estimator for a wider range of f 0 f_{0} , but may not be possible. Thus, methods that balance X i X_{i} “approximately”, or reduce the “imbalance” (i.e., differences in the means) to a level within some small threshold, have entered the literature in recent years (e.g, Zubizarreta, 2015 ; Wang and Zubizarreta, 2020 ). This approach allows weights that instead balance high-dimensional transformations of X i X_{i} , such as basis functions from a reproducing kernel Hilbert space (e.g, Kallus, 2020 ; Hirshberg et al., 2021 ; Wong and Chan, 2018 ; Hazlett, 2020 ; Tarr and Imai, 2021 ), linear functions of which can approximate any smooth f 0 f_{0} . Approximate balancing weights may thus avoid bias stemming from misspecifying f 0 f_{0} . However, feasibility remains an issue — τ ^ wdim \hat{\tau}_{\mathrm{wdim}} is still susceptible to bias because these weights leave imbalance in X i X_{i} , with the average imbalance across X i X_{i} typically increasing as does its dimension. Further, imbalance in certain elements of X i X_{i} can be more damaging than in others, depending on their influence on Y i Y_{i} . These concerns require one to proceed cautiously when exchanging X i X_{i} with its high-dimensional transformation or prioritizing balance in select dimensions of X i X_{i} , if at all.

But while balance in X i X_{i} , or a transformation of it, may be sufficient for an unbiased τ ^ wdim \hat{\tau}_{\mathrm{wdim}} , it is not required — in fact, all that is required is exact balance in f 0 ​ ( X i ) f_{0}(X_{i}) , i.e., equality of the means of f 0 ​ ( X i ) f_{0}(X_{i}) in the treated and control groups after weighting. From this perspective, seeking balance in X i X_{i} is excessive. To illustrate, were f 0 f_{0} linear in X i X_{i} , balance in one linear function of X i X_{i} (i.e., f 0 f_{0} ) would be sufficient, but weights that balance X i X_{i} also balance all linear functions of it — an inefficient strategy at best, and can hinder proper balance in f 0 ​ ( X i ) f_{0}(X_{i}) . This perspective motivates Targeted Function Balancing (TFB), which more directly targets balance in f 0 ​ ( X i ) f_{0}(X_{i}) by estimating it with f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) , and choosing weights that balance functions near f ^ 0 \hat{f}_{0} , in hopes that f 0 f_{0} is among them. In short, this yields approximate balance in X i X_{i} and f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) , with the estimated variance of f ^ 0 \hat{f}_{0} determining how much balance in X i X_{i} is sufficient.

More specifically, TFB has several notable characteristics. First, it is an approximate balancing method, so it may exchange X i X_{i} with a high-dimensional transformation of X i X_{i} . This includes basis functions from a reproducing kernel Hilbert space, building on the developing literature of weights that draw on them (e.g., Kallus, 2020 ; Hazlett, 2020 ; Wong and Chan, 2018 ; Hirshberg et al., 2021 ; Huang et al., 2006 ; Zhao, 2019 ; Tarr and Imai, 2021 ), by estimating f 0 f_{0} with kernel regularized least squares ( Hainmueller and Hazlett, 2014 ). Further, TFB is not limited to regression estimators with linear representations — for example, we apply Bayesian Additive Regression Trees ( Hill, 2011 ) in our demonstrations here. However, TFB offers a solution to feasibility concerns by narrowing the function space that the weights seek balance in, that is, from all (linear) functions of X i X_{i} (and its tranformations), to those probabilistically near f ^ 0 \hat{f}_{0} per its estimated variance. Second, and relatedly, TFB primarily seeks balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) , but additionally seeks balance in X i X_{i} to safeguard against uncertainty in f ^ 0 \hat{f}_{0} , and to a degree deemed necessary by the estimated variance of f ^ 0 \hat{f}_{0} . Consequently, and in contrast to traditions that advocate for good balance on every covariate (e.g., Stuart, 2010 ), TFB may intentionally leave imbalance in dimensions of X i X_{i} because they have little to no influence on Y i Y_{i} , or to offset imbalances in other dimensions. This can improve feasibility and yield efficiency gains without introducing bias, as is demonstrated below. Third, the estimated variance of f ^ 0 \hat{f}_{0} determines how to prioritize balance in each dimension of X i X_{i} , a feature that can be exploited to great effect by estimating f 0 f_{0} with sparsity (e.g., the LASSO). Fourth, and finally, TFB’s weights are entirely defined by the choice of regression estimator (i.e., f ^ 0 \hat{f}_{0} ) and an estimator for its variance, thus turning the problem of how best to balance the covariates into how best to model the outcome.

Combining a f ^ 0 \hat{f}_{0} and weights to estimate treatment effects is a well-studied research area. It is essential to the augmented (weighted) estimator, the typical form of doubly-robust estimators (e.g., Robins et al., 1994 ; Robins and Rotnitzky, 1995 ; van der Laan and Rubin, 2006 ; Tan, 2010 ; Rotnitzky et al., 2012 ; Chernozhukov et al., 2018 ), which are consistent in a propensity score weights setting when the investigator has correctly specified f 0 f_{0} or π \pi . Augmented estimators have also been applied with approximate balancing weights (e.g. Athey et al., 2018 , Hirshberg and Wager, 2021 ). In fact, TFB performs similarly to an augmented estimator in practice, so this estimator is given particular attention below. Other methods that use a f ^ 0 \hat{f}_{0} in conjunction with weights include those that allow a f ^ 0 \hat{f}_{0} to inform which dimensions of X i X_{i} to prioritize balance in, or to use to estimate π \pi for propensity score weights (e.g., Shortreed and Ertefaie, 2017 ; Kuang et al., 2017 ; Ning et al., 2020 ), and methods that expand on prognostic score theory from Hansen, 2008 (e.g., Leacy and Stuart, 2014 ; Antonelli et al., 2018 ), which supports seeking balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) . TFB contributes to this literature by letting the estimated variance of f ^ 0 \hat{f}_{0} determine how to prioritize balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) over X i X_{i} , and in certain dimensions of X i X_{i} over others.

To outline, Section 2 details notation and assumptions, and reviews reproducing kernel Hilbert spaces, which appear throughout, and Section 3 expands on the motivation for TFB. Section 4 introduces TFB (and TFI), demonstrates its merits through simulation and in an application to the 2016 American Causal Inference Conference challenge data ( Dorie et al., 2019 ). Section 4 also illuminates the connection between TFB and augmented estimation. Section 5 then applies TFB to the National Supported Work Demonstration ( LaLonde, 1986 ) data, and Section 6 concludes.


## 2 Background


## 2.1 Notation and assumptions

Let i ∈ { 1 , … , n } i\in\{1,\dots,n\} index the units of observation and let p ⁡ ( ⋅ ) p(\cdot) be the density function of an arbitrary random variable. Define D i ∈ { 0 , 1 } D_{i}\in\{0,1\} to be an indicator variable for receiving the treatment, with n t n_{t} the number of treated units and n c = n − n t n_{c}=n-n_{t} the number of control units. Additionally, let D = [ D 1 ​ … ​ D n ] ⊤ D=[D_{1}\ \dots\ D_{n}]^{\top} be the vector of treatment statuses for the sample, and let the first n c n_{c} units make up the control group (i.e., 1 ≤ i ≤ n c 1\leq i\leq n_{c} are the indices for the control units and n c + 1 ≤ i ≤ n n_{c}+1\leq i\leq n are the indices for the treated units). Then, let X i X_{i} be a P P -dimensional vector of covariates and let X X be the matrix of X i X_{i} for the sample.

In accordance with the potential outcomes framework ( Splawa-Neyman et al., 1990 ; Rubin, 1974 ) , Y i ​ ( 0 ) Y_{i}(0) is the outcome if control and Y i ​ ( 1 ) Y_{i}(1) is the outcome if treated, so Y i = Y i ​ ( D i ) Y_{i}=Y_{i}(D_{i}) is observed. Implicit here is the stable unit treatment value assumption (SUTVA), that the potential outcomes for unit i i are not functions of the treatment statuses of other units, and that each treatment status is administered the same across the units. Further, the tuples ( X i , D i , Y i ​ ( 0 ) , Y i ​ ( 1 ) ) (X_{i},D_{i},Y_{i}(0),Y_{i}(1)) are assumed independent and identically distributed (iid).

Of particular importance to TFB is the conditional expectation function of Y i ​ ( d ) Y_{i}(d) given X i X_{i} , defined here as f d ​ ( X i ) = 𝔼 ⁡ [ Y i ​ ( d ) | X i ] f_{d}(X_{i})=\mathbbm{E}[Y_{i}(d)\ |\ X_{i}] , where 𝔼 ⁡ ( ⋅ ) \mathbbm{E}(\cdot) is the expectation over p ⁡ ( ⋅ ) p(\cdot) (i.e., the super-population). This allows the model:

where ϵ i ​ ( d ) \epsilon_{i}(d) is an error term associated with potential outcome Y i ​ ( d ) Y_{i}(d) . Although TFB is not limited to models with linear representations, we will often consider the setting where f d f_{d} is linear in X i X_{i} ,

( 3 ) appears restrictive because X i X_{i} has been defined thus far as a vector of untransformed covariates. However, exchanging X i X_{i} with, or allowing it to include, its nonlinear transformations (e.g., polynomial terms, or basis functions) makes this representation of f d f_{d} quite general, and is the setting in which the linear form of TFB largely operates.

This paper assumes throughout the absence of unobserved confounding in the relationship between D i D_{i} and Y i Y_{i} , otherwise known as conditional ignorability:

( Y i ​ ( 0 ) , Y i ​ ( 1 ) ) ⊧ D i | X i (Y_{i}(0),Y_{i}(1))\ \rotatebox[origin]{90.0}{$\models$}\ D_{i}\ |\ X_{i}

Note that the conditional independence in Assumption 1 extends to the ϵ i ​ ( d ) \epsilon_{i}(d) and D i D_{i} (i.e., ( ϵ i ​ ( 0 ) , ϵ i ​ ( 1 ) ) ⊧ D i | X i (\epsilon_{i}(0),\epsilon_{i}(1))\ \rotatebox[origin]{90.0}{$\models$}\ D_{i}\ |\ X_{i} ), as ( 2 ) implies that ϵ i ​ ( d ) = Y i ​ ( d ) − f d ​ ( X i ) \epsilon_{i}(d)=Y_{i}(d)-f_{d}(X_{i}) .

Unobserved confounders, which would violate Assumption 1 , are often a concern in real-data settings, but are beyond the scope of this paper. However, sensitivity analysis to unobserved confounders is a growing field of research, particularly for estimators that use weights — see Hong et al., 2021 and Soriano et al., 2021 for examples.

This paper primarily considers the average treatment effect on the treated (ATT),

However, Appendix A adapts TFB to estimate the average treatment effect, ATE = 𝔼 ⁡ [ Y i ​ ( 1 ) − Y i ​ ( 0 ) ] \mathrm{ATE}=\mathbbm{E}[Y_{i}(1)-Y_{i}(0)] , and the average treatment effect on the controls, ATC = 𝔼 ⁡ [ Y i ​ ( 1 ) − Y i ​ ( 0 ) | D i = 0 ] \mathrm{ATC}=\mathbbm{E}[Y_{i}(1)-Y_{i}(0)\ |\ D_{i}=0] .

Were it observed, the sample average treatment effect on the treated (SATT),

would be the ideal estimator for the ATT, but the Y i ​ ( 0 ) Y_{i}(0) are unobserved for treated units without strong assumptions. The class of estimators studied here thus replaces 1 n t ∑ i : D i = 1 Y i ( 0 ) \frac{1}{n_{t}}\sum_{i:D_{i}=1}Y_{i}(0) in SATT with a weighted average of the Y i ​ ( 0 ) Y_{i}(0) for the control units, 1 n c ∑ i : D i = 0 w i Y i ( 0 ) \frac{1}{n_{c}}\sum_{i:D_{i}=0}w_{i}Y_{i}(0) for nonnegative weights w i w_{i} . The resulting weighted difference in means estimator has the form

where w w is an arbitrary vector of nonnegative weights for control units,

These weights will have mean 1 (i.e., 1 n c ∑ i : D i = 0 w i = 1 \frac{1}{n_{c}}\sum_{i:D_{i}=0}w_{i}=1 ) in most settings considered here. However, this condition will not be required, unless otherwise noted. Section 3 discusses the conditions that w w must satisfy for τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) to be unbiased.


## 2.2 Background on reproducing kernel Hilbert spaces

The unbiasedness of many τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) in the literature hinges on the specification of f 0 f_{0} . Thus, some, including this paper, have turned to reproducing kernel Hilbert spaces (RKHS) to characterize a large space of functions from which f 0 f_{0} , or an arbitrarily close approximation, could come. This section therefore provides a brief review of the relevant points in RKHS. For a more extensive review, see Wainwright, 2019 .

Background on “positive semi-definite kernel functions” is first required. A positive semi-definite kernel function, 𝒦 : ℝ P × ℝ P → ℝ \mathcal{K}:\mathbb{R}^{P}\times\mathbb{R}^{P}\rightarrow\mathbb{R} , is a symmetric function such that for all possible choices of { x 1 , … , x m } ⊆ ℝ P \{x_{1},\dots,x_{m}\}\subseteq\mathbb{R}^{P} for arbitrary m m , the m × m m\times m matrix with i ​ j ij th element equal to 𝒦 ⁡ ( x i , x j ) \mathcal{K}(x_{i},x_{j}) is positive semi-definite. Per Hazlett, 2020 , it is helpful to interpret 𝒦 \mathcal{K} as a similarity score. For example, the 𝒦 \mathcal{K} primarily employed here is the Gaussian kernel, 𝒦 ⁡ ( x i , x j ) = e − ‖ x i − x j ‖ 2 2 b \mathcal{K}(x_{i},x_{j})=e^{-\frac{||x_{i}-x_{j}||_{2}^{2}}{b}} for some bandwidth parameter b b . This kernel’s range is 0 to 1, with 𝒦 ⁡ ( x i , x j ) = 1 \mathcal{K}(x_{i},x_{j})=1 only when x i = x j x_{i}=x_{j} (i.e., when x i x_{i} and x j x_{j} are as similar as can be), and 𝒦 ⁡ ( x i , x j ) \mathcal{K}(x_{i},x_{j}) approaches 0 as ‖ x i − x j ‖ 2 → ∞ ||x_{i}-x_{j}||_{2}\rightarrow\infty (i.e., as x i x_{i} and x j x_{j} diverge).

A RKHS, H ⁡ ( 𝒦 ) H(\mathcal{K}) , is then the unique Hilbert space of functions h : ℝ P → ℝ h:\mathbb{R}^{P}\rightarrow\mathbb{R} that contains 𝒦 ⁡ ( ⋅ , x ) \mathcal{K}(\cdot,x) for ∀ x ∈ ℝ P \forall x\in\mathbb{R}^{P} , and has the inner product ⟨ ⋅ , ⋅ ⟩ H ⁡ ( 𝒦 ) : H ⁡ ( 𝒦 ) × H ⁡ ( 𝒦 ) → ℝ \langle\cdot,\cdot\rangle_{H(\mathcal{K})}:H(\mathcal{K})\times H(\mathcal{K})\rightarrow\mathbb{R} satisfying the Reproducing Property :

and norm ‖ h ‖ H ⁡ ( 𝒦 ) = ⟨ h , h ⟩ H ⁡ ( 𝒦 ) ||h||_{H(\mathcal{K})}=\sqrt{\langle h,h\rangle_{H(\mathcal{K})}} . If f 0 ∈ H ⁡ ( 𝒦 ) f_{0}\in H(\mathcal{K}) , then the Reproducing Property allows the representation f 0 ​ ( X i ) = K i ​ α 0 f_{0}(X_{i})=K_{i}\alpha_{0} for K i = [ 𝒦 ( X i , X 1 ) ⋯ 𝒦 ( X i , X n ) ] K_{i}=[\mathcal{K}(X_{i},X_{1})\ \cdots\ \mathcal{K}(X_{i},X_{n})] and some α 0 ∈ ℝ n \alpha_{0}\in\mathbb{R}^{n} (see Wainwright, 2019 for proof). Thus, within the sample, any function in H ⁡ ( 𝒦 ) H(\mathcal{K}) can be expressed as a linear function of K i K_{i} . This representation can be quite powerful, depending on the choice of 𝒦 \mathcal{K} . For example, for some choices (e.g., the Gaussian kernel for any b b ), a function in H ⁡ ( 𝒦 ) H(\mathcal{K}) can approximate any smooth function to an arbitrarily close degree. 1 1 1 H ⁡ ( 𝒦 ) H(\mathcal{K}) can be represented in several ways. The first is the closure of the function space { ∑ j = 1 m α ( j ) 𝒦 ( x j , ⋅ ) | ∀ m ∈ ℤ ≥ 0 , ∀ x j ∈ ℝ P , ∀ α ( j ) ∈ ℝ } \{\sum_{j=1}^{m}\alpha^{(j)}\mathcal{K}(x_{j},\cdot)\ |\ \forall m\in\mathbb{Z}^{\geq 0},\forall x_{j}\in\mathbb{R}^{P},\forall\alpha^{(j)}\in\mathbb{R}\} , i.e., arbitrary linear combinations of 𝒦 ⁡ ( x j , ⋅ ) \mathcal{K}(x_{j},\cdot) for arbitrarily many x j x_{j} . This representation illuminates why f 0 ​ ( X i ) = K i ​ α 0 f_{0}(X_{i})=K_{i}\alpha_{0} , but does not explain why, for some 𝒦 \mathcal{K} , functions in H ⁡ ( 𝒦 ) H(\mathcal{K}) can approximate any smooth function. This is more easily understood from the alternate representation of H ⁡ ( 𝒦 ) = { ∑ ℓ = 1 ∞ β ( ℓ ) ​ ϕ 𝒦 ( ℓ ) | ∑ ℓ = 1 ∞ ( β ( ℓ ) ) 2 < ∞ ​ and ​ ∑ ℓ = 1 ∞ ( β ( ℓ ) ) 2 / μ 𝒦 ( ℓ ) < ∞ } H(\mathcal{K})=\{\sum_{\ell=1}^{\infty}\beta^{(\ell)}\phi_{\mathcal{K}}^{(\ell)}\ |\ \sum_{\ell=1}^{\infty}(\beta^{(\ell)})^{2}<\infty\ \text{and}\ \sum_{\ell=1}^{\infty}(\beta^{(\ell)})^{2}/\mu_{\mathcal{K}}^{(\ell)}<\infty\} where ϕ 𝒦 ( ℓ ) \phi^{(\ell)}_{\mathcal{K}} and μ 𝒦 ( ℓ ) \mu^{(\ell)}_{\mathcal{K}} are eigenfunctions and eigenvalues, respectively, associated with 𝒦 \mathcal{K} , i.e., H ⁡ ( 𝒦 ) H(\mathcal{K}) contains linear functions of (potentially) infinite dimensional ϕ 𝒦 = [ ϕ 𝒦 ( 1 ) ​ ϕ 𝒦 ( 2 ) ​ … ] ⊤ \phi_{\mathcal{K}}=[\phi^{(1)}_{\mathcal{K}}\ \phi^{(2)}_{\mathcal{K}}\ \dots]^{\top} . If ϕ 𝒦 \phi_{\mathcal{K}} is flexible, then it is plausible that linear functions of it could approximate any smooth function, just like a high degree polynomial might.

Finally, extra notation is needed. Let K K be the n × n n\times n matrix with i ​ j ij th element 𝒦 ⁡ ( X i , X j ) \mathcal{K}(X_{i},X_{j}) , otherwise known as the “gram” matrix for the full sample, and let K i K_{i} be the i i th row of K K .

From a similarity score perspective, K i K_{i} holds unit i i ’s similarity scores to each unit in the data. Then, letting K c K_{c} be the first n c n_{c} columns of K K with rows K i ​ c = [ 𝒦 ( X i , X 1 ) ⋯ 𝒦 ( X i , X n c ) ] K_{ic}=[\mathcal{K}(X_{i},X_{1})\ \cdots\ \mathcal{K}(X_{i},X_{n_{c}})] , the K i ​ c K_{ic} may be thought of as holding unit i i ’s similarity scores to each control unit in the data. Accordingly, let K t K_{t} be the last n t n_{t} columns of K K with rows K i ​ t = [ 𝒦 ( X i , X n c + 1 ) ⋯ 𝒦 ( X i , X n ) ] K_{it}=[\mathcal{K}(X_{i},X_{n_{c}+1})\ \cdots\ \mathcal{K}(X_{i},X_{n})] .

Finally, let K c ​ c K_{cc} be the first n c n_{c} rows of K c K_{c} and let K t ​ c K_{tc} the last n t n_{t} rows of K c K_{c} . K c ​ c K_{cc} is also the gram matrix for the control group.


## 3 Motivation for TFB

This section motivates TFB by reframing existing approaches in the weighting literature as decisions on a set of potential f 0 f_{0} to seek balance in. TFB builds on this idea by letting a f ^ 0 \hat{f}_{0} , an estimate of f 0 f_{0} , and its estimated variance inform this decision. Section 3.1 first reviews the role that f 0 f_{0} plays in the conditions the weights must satisfy for τ ^ wdim \hat{\tau}_{\mathrm{wdim}} to be unbiased.


## 3.1 Desirable conditions for the weights

We first define what we refer to as the “weighting condition” (WC),

and its empirical analog, which we refer to as the “empirical weighting condition” (EWC),

In words, WC and EWC require that the means of f 0 ​ ( X i ) f_{0}(X_{i}) be equated in expectation or empirically.

EWC is given particular focus in TFB, so we discuss it first. First define the imbalance, or difference in the means, in a function of X i X_{i} as

where g g is an arbitrary vector-valued function. How far the weights are from satisfying EWC, to be referred to as the “EWC Bias”, then has an intuitive form as the imbalance in f 0 ​ ( X i ) f_{0}(X_{i}) :

Proposition 1 below states that, under certain conditions, the expectation of the EWC Bias is exactly the bias of τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) , and thus τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) is unbiased for the ATT under EWC:

Given (i) Assumption 1 and (ii) that each pair of w i w_{i} and Y i ​ ( 0 ) Y_{i}(0) are independent given X X and D D (i.e., w i ⊧ Y i ​ ( 0 ) | X , D w_{i}\rotatebox[origin]{90.0}{$\models$}Y_{i}(0)\ |\ X,D for ∀ i \forall i ),

and, consequently, τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) is unbiased for the ATT (i.e., 𝔼 ​ [ τ ^ wdim ​ ( w ) ] = ATT \mathbbm{E}[\hat{\tau}_{\mathrm{wdim}}(w)]=\mathrm{ATT} ) under EWC.

Proof is given in Appendix D.1 . Of note is that Proposition 1 requires each pair of w i w_{i} and Y i ​ ( 0 ) Y_{i}(0) to be independent given X X and D D . As will be discussed later (in Section 4.5 ), TFB’s weights depend on the Y i Y_{i} , but can be implemented in a way such that this condition holds. Many methods in the literature (e.g., Hainmueller, 2012 ; Zubizarreta, 2015 ; Hazlett, 2020 ) choose weights that are “honest”, or entirely defined by X X and D D , which leaves all of the w i w_{i} independent of all of the Y i Y_{i} given X X and D D , a stronger condition than is required for Proposition 1 .

Note also that EWC (and WC) do not require complete overlap in the conditional distributions of X i X_{i} , or

where π ⁡ ( X i ) = p ⁡ ( D i = 1 | X i ) \pi(X_{i})=p(D_{i}=1\ |\ X_{i}) is the propensity score. This is traditionally assumed in settings with propensity score weights ( Rosenbaum and Rubin, 1983 ). Instead, satisfying EWC with positive weights with mean 1 requires a far weaker overlap condition: that the average f 0 ​ ( X i ) f_{0}(X_{i}) in the treated group (i.e., 1 n t ∑ i : D i = 1 f 0 ( X i ) \frac{1}{n_{t}}\sum_{i:D_{i}=1}f_{0}(X_{i}) ) is within the range of the f 0 ​ ( X i ) f_{0}(X_{i}) among the control group. We thus forgo the traditional overlap assumption in ( 13 ). See also Appendix C.5 for a simulated example where TFB is effectively unbiased, but traditional overlap is violated.

While not as central to TFB, WC is a similarly desirable condition. Proposition 2 states that weights that satisfy WC yield an unbiased τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) under certain conditions.

Given (i) Assumption 1 and (ii) w i = w ⁡ ( X i , D i ) w_{i}=w(X_{i},D_{i}) for a weight function w ⁡ ( ⋅ ) w(\cdot) , the resulting τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) is unbiased for the ATT if the weights satisfy WC.

Proof is given in Appendix D.2 . Although less of a focus for TFB, Proposition 2 again emphasizes the importance of mean balance in f 0 f_{0} , this time in expectation.


## 3.2 Building blocks

This section reviews two families of weighting procedures in the literature: propensity score and balancing weights, the latter of which includes TFB. Within each family, focus is given to the tension between the assumptions on f 0 f_{0} required for unbiasedness and the weights’ feasibility.

WC is satisfied by w i = p ⁡ ( X i | D i = 1 ) p ⁡ ( X i | D i = 0 ) = p ⁡ ( D i = 0 ) p ⁡ ( D i = 1 ) ​ π ⁡ ( X i ) 1 − π ⁡ ( X i ) w_{i}=\frac{p(X_{i}\ |\ D_{i}=1)}{p(X_{i}\ |\ D_{i}=0)}=\frac{p(D_{i}=0)}{p(D_{i}=1)}\frac{\pi(X_{i})}{1-\pi(X_{i})} . This offers motivation for propensity score weights ( Rosenbaum and Rubin, 1983 ) — were π ^ ​ ( X i ) \hat{\pi}(X_{i}) to consistently estimate π ⁡ ( X i ) \pi(X_{i}) , then w ^ i = n c n t ​ π ^ ​ ( X i ) 1 − π ^ ​ ( X i ) \hat{w}_{i}=\frac{n_{c}}{n_{t}}\frac{\hat{\pi}(X_{i})}{1-\hat{\pi}(X_{i})} yields a consistent τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) . 2 2 2 A τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) with w ^ i = n c ( ∑ i : D i = 0 π ^ ​ ( X i ) 1 − π ^ ​ ( X i ) ) − 1 π ^ ​ ( X i ) 1 − π ^ ​ ( X i ) \hat{w}_{i}=n_{c}(\sum_{i:D_{i}=0}\frac{\hat{\pi}(X_{i})}{1-\hat{\pi}(X_{i})})^{-1}\frac{\hat{\pi}(X_{i})}{1-\hat{\pi}(X_{i})} is also consistent, allowing 1 n c ∑ i : D i = 0 w ^ i = 1 \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}=1 . Of note is that propensity score weights satisfy WC (approximately) for any f 0 f_{0} . However, this comes at the price of a specification of π \pi . An incorrect specification may lead to biased τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) (e.g., Kang and Schafer, 2007 ).

But satisfying WC or EWC for any f 0 f_{0} is unnecessary if one has prior knowledge about f 0 f_{0} . For example, if f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} then weights that achieve exact balance in X i X_{i} ,

satisfy EWC. This motivates balancing weights, which attempt to make the imbalance in X X small. One subfamily, originating from calibration in the survey literature (e.g., Deming and Stephan, 1940 ; Deville and Särndal, 1992 ), is:

for some δ = [ δ ( 1 ) ​ … ​ δ ( P ) ] ≥ 0 \delta=[\delta^{(1)}\ \dots\ \delta^{(P)}]\geq 0 , and B ⁡ ( w ) B(w) is a function that controls the variance of w w or distance from base weights. The constraints 1 n c ∑ i : D i = 0 w i = 1 \frac{1}{n_{c}}\sum_{i:D_{i}=0}w_{i}=1 and w i ≥ 0 w_{i}\geq 0 are typically added.

A common approach is to require exact balance on X X through BAL1 by setting δ = 0 \delta=0 (e.g., Chan et al., 2016 ). A notable example is Entropy Balancing ( Hainmueller, 2012 ), which chooses B ⁡ ( w ) B(w) to be the (negative) entropy, 1 n c ∑ i : D i = 0 w i log ( w i ) \frac{1}{n_{c}}\sum_{i:D_{i}=0}w_{i}\mathrm{log}(w_{i}) . However, exact balance exhibits two shortcomings — one of specification and one of feasibility. On specification, the resulting τ ^ wdim ​ ( w ^ BAL1 ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}_{\text{BAL1}}) is only assured to be unbiased when f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} . On feasibility, weights that achieve the exact balance in ( 14 ) may not exist (e.g., when X i X_{i} is of large dimension) or may be extreme, resulting in a high variance τ ^ wdim ​ ( w ^ BAL1 ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}_{\text{BAL1}}) . Further, these issues compound each other. One may expand X i X_{i} to include its nonlinear transformations, finding exact balance has become infeasible.

These concerns have motivated approximate balancing weights. Within the BAL1 framework, Zubizarreta, 2015 and Wang and Zubizarreta, 2020 relax the exact balance conditions by letting δ > 0 \delta>0 . If f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} , then δ \delta presents a bias-variance tradeoff: smaller δ ( ℓ ) \delta^{(\ell)} reduce the bias of the resulting τ ^ wdim ​ ( w ^ BAL1 ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}_{\text{BAL1}}) , but also shrink the space of solutions for the weights, which may increase the variance of τ ^ wdim ​ ( w ^ BAL1 ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}_{\text{BAL1}}) . The choice of δ \delta is thus paramount to the performance of BAL1 . Additionally, if f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} , weights found by BAL1 bound the EWC Bias for the “worst-case” β 0 \beta_{0} , or the β 0 \beta_{0} that yields the most bias, as

where the first inequality in ( 15 ) becomes an equality when β 0 \beta_{0} is in the direction of the leftover imbalance. Thus, X i X_{i} and δ \delta can be thought of as defining a space of functions from which the worst-case f 0 f_{0} may come (i.e., ℱ = { x ⊤ ​ β | | β ( ℓ ) | ≤ δ ( ℓ ) ​ ‖ β 0 ‖ 2 ‖ δ ‖ 2 } \mathcal{F}=\{x^{\top}\beta\ |\ |\beta^{(\ell)}|\leq\delta^{(\ell)}\frac{||\beta_{0}||_{2}}{||\delta||_{2}}\} ). Another subfamily of balancing procedures incorporates this idea directly, finding low variance weights that minimize the EWC Bias for the worst-case f 0 f_{0} over some space of functions, ℱ \mathcal{F} ,

where the constraints 1 n c ∑ i : D i = 0 w i = 1 \frac{1}{n_{c}}\sum_{i:D_{i}=0}w_{i}=1 and w i ≥ 0 w_{i}\geq 0 are usually added. Analogous to X i X_{i} and δ \delta in BAL1 , the parametrization of ℱ \mathcal{F} determines the complexity of f 0 f_{0} that BAL2 aims to balance, and the size of ℱ \mathcal{F} determines how to prioritize minimizing the squared EWC Bias relative to B ⁡ ( w ) B(w) . 3 3 3 For example, if ℱ = { x ⊤ ​ β | ‖ β ‖ 2 ≤ C } \mathcal{F}=\{x^{\top}\beta\ |\ ||\beta||_{2}\leq C\} , the objective function in BAL2 becomes C 2 ​ ‖ imbal ⁡ ( w , X , D ) ‖ 2 2 + B ⁡ ( w ) C^{2}||\mathrm{imbal}(w,X,D)||_{2}^{2}+B(w) . The resulting procedure attempts to balance the worst-case linear function of X i X_{i} , which is determined by overall balance in X i X_{i} . C C determines how much balance in X i X_{i} is prioritized over B ⁡ ( w ) B(w) .

By removing the requirement of exact balance, approximate balancing weights can be made to appear robust to a wide range of f 0 f_{0} by allowing a high-dimensional X i X_{i} or, analogously in BAL2 , a flexible ℱ \mathcal{F} . For example, some (e.g., Kallus, 2020 ; Hazlett, 2020 ; Wong and Chan, 2018 , Hirshberg et al., 2021 ; Zhao, 2019 ; Tarr and Imai, 2021 ) assume f 0 f_{0} to be of a RKHS, applying the representation f 0 ​ ( X i ) = K i ​ α 0 f_{0}(X_{i})=K_{i}\alpha_{0} , and approximately balance K i K_{i} . However, the optimal ways to choose δ \delta in BAL1 or ℱ \mathcal{F} in BAL2 are unsolved problems, despite data-driven proposals available (e.g., Wang and Zubizarreta, 2020 and Chattopadhyay et al., 2020 for BAL1 ; Kallus, 2020 and Wong and Chan, 2018 for BAL2 ). Furthermore, BAL2 estimators that use a data-driven ℱ \mathcal{F} often center it at the zero function, f ⁡ ( x ) = 0 f(x)=0 . Kallus, 2020 , for example, uses a ball in a RKHS: ℱ = { h ∈ H ⁡ ( 𝒦 ) | ‖ h ‖ H ⁡ ( 𝒦 ) ≤ C } \mathcal{F}=\{h\in H(\mathcal{K})\ |\ ||h||_{H(\mathcal{K})}\leq C\} for a data-driven C C . The worst-case function in ℱ \mathcal{F} may then be in the opposite direction of, or orthogonal to, f 0 f_{0} in H ⁡ ( 𝒦 ) H(\mathcal{K}) (i.e., ⟨ ⋅ , f 0 ⟩ H ⁡ ( 𝒦 ) = 0 \langle\cdot,f_{0}\rangle_{H(\mathcal{K})}=0 ). 4 4 4 An orthogonal function when f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} is perhaps illustrative. If X i = [ X i ( 1 ) ​ X i ( 2 ) ] ⊤ X_{i}=[X_{i}^{(1)}\ X_{i}^{(2)}]^{\top} and β 0 = [ 1 0 ] ⊤ \beta_{0}=[1\ 0]^{\top} , a function orthogonal to f 0 f_{0} would be f ⟂ ​ ( X i ) = X i ⊤ ​ β ⟂ f_{\perp}(X_{i})=X_{i}^{\top}\beta_{\perp} where β ⟂ = [ 0 1 ] ⊤ \beta_{\perp}=[0\ 1]^{\top} . Therefore, while only X i ( 1 ) X_{i}^{(1)} has any marginal effect on Y i ​ ( 0 ) Y_{i}(0) , balancing the worst-case linear function of X i X_{i} would involve balancing functions that disregard any marginal effect of X i ( 1 ) X_{i}^{(1)} on Y i ​ ( 0 ) Y_{i}(0) . Balance on these orthogonal functions would not grant further bias reduction, were balance in f 0 ​ ( X i ) f_{0}(X_{i}) to remain constant. However, requiring good balance on these functions would, at least, increase the variance of the resulting estimator, and could, at worst, distract the weights from obtaining good balance on f 0 ​ ( X i ) f_{0}(X_{i}) . Further, as ℱ \mathcal{F} is allowed to be larger and more flexible, this inefficiency could be exacerbated. This concern provides the main motivation for TFB, which can be framed as BAL2 and seeks a ℱ \mathcal{F} that contains only functions close to f 0 f_{0} with a user-chosen probability (e.g., 0.95).


## 4 Framework for TFB


## 4.1 A novel balance diagnostic

This section introduces Targeted Function Imbalance (TFI), a balance diagnostic that TFB minimizes over the w i w_{i} , and approximates the EWC Bias using a f ^ 0 \hat{f}_{0} and its estimated variance.

To motivate TFI, we consider the setting where f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} . Recall that exchanging X i X_{i} with, or allowing it to include, its nonlinear transformations (e.g., basis functions) makes this representation of f 0 f_{0} quite general. The magnitude of the EWC Bias then simplifies to

Then, letting β ^ 0 \hat{\beta}_{0} be an arbitrary estimate of β 0 \beta_{0} , consider ( 16 ) for the worst-case β 0 \beta_{0} close to β ^ 0 \hat{\beta}_{0} with some high level of probability (e.g., 0.95):

where S q ⊆ ℝ P S_{q}\subseteq\mathbb{R}^{P} is a set that contains 0 and p ⁡ ( β ^ 0 − β 0 ∈ S q ) ≈ q p(\hat{\beta}_{0}-\beta_{0}\in S_{q})\approx q for some q q ( q q will be left arbitrary here, but Section 4.4 studies it more closely). In other words, S q S_{q} is set of small deviations such that, with probability approximately q q , β 0 \beta_{0} can be recovered by subtracting one of these small deviations from β ^ 0 \hat{\beta}_{0} . Clearly, S q S_{q} will be defined by the distribution of β ^ 0 \hat{\beta}_{0} .

Proceeding further thus requires a choice of β ^ 0 \hat{\beta}_{0} . To motivate the final expression for TFI, consider the setting where β ^ 0 \hat{\beta}_{0} is the OLS estimate using only the control units. β ^ 0 \hat{\beta}_{0} then has an easily computed estimated variance in the sandwich variance estimator ( White, 1980 ) ,

where V ^ β 0 − 1 2 ​ ( β ^ 0 − β 0 ) ​ → 𝑑 ​ 𝒩 ​ ( 0 , I P ) \hat{V}_{\beta_{0}}^{-\frac{1}{2}}(\hat{\beta}_{0}-\beta_{0})\overset{d}{\rightarrow}\mathcal{N}(0,I_{P}) under iid data. Here, a logical S q S_{q} is one that, after being transformed by V ^ β 0 − 1 2 \hat{V}_{\beta_{0}}^{-\frac{1}{2}} , becomes a ball centered at the origin in which a 𝒩 ⁡ ( 0 , I P ) \mathcal{N}(0,I_{P}) falls with probability q q . This yields S q = { V ^ β 0 1 2 ​ x ∈ ℝ P | ‖ x ‖ 2 ≤ Q q ​ ( 𝒳 P 2 ) } S_{q}=\{\hat{V}_{\beta_{0}}^{\frac{1}{2}}x\in\mathbb{R}^{P}\ |\ ||x||_{2}\leq\sqrt{Q_{q}(\mathcal{X}^{2}_{P})}\} , where Q q ​ ( 𝒳 P 2 ) Q_{q}(\mathcal{X}^{2}_{P}) is the q q th quantile of a chi-squared random variable with P P degrees of freedom, simplifying ( 17 ) to TFI:

Although the above derivation uses OLS as motivation, we instead experiment below applying TFI with non-OLS regressions, simply replacing β ^ 0 \hat{\beta}_{0} with a different estimate, and V ^ β 0 \hat{V}_{\beta_{0}} with a suitable variance estimator. To preview, we primarily consider three forms of TFI. The first form applies kernel regularized least squares ( Hainmueller and Hazlett, 2014 ), the second applies LASSO regression, and the third applies Bayesian Additive Regression Trees ( Hill, 2011 ). As will be discussed, applying these regressions allows TFB to exhibit desirable tendencies in finite samples even without clean asymptotic guarantees from OLS under a correctly specified linear model.


## 4.2 Choosing weights in TFB

This section introduces TFB, which finds low variance weights that minimize TFI. TFB, like Kallus, 2020 , considers minimizing the conditional mean squared error of τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) as an estimate of the SATT,

where the constant does not depend on the weights. Define TFB then as

where the objective function in the above approximates the EWC Bias in ( 20 ) with TFI, and substitutes the σ i 2 ​ ( 0 ) \sigma^{2}_{i}(0) with σ ^ 2 ( 0 ) = 1 n c ∑ i : D i = 0 ( Y i − X i ⊤ β ^ 0 ) 2 \hat{\sigma}^{2}(0)=\frac{1}{n_{c}}\sum_{i:D_{i}=0}(Y_{i}-X_{i}^{\top}\hat{\beta}_{0})^{2} . The objective function is convex, and MOSEK (through the Rmosek package in R ) was used to solve this problem in all demonstrations here.

A key consequence of this is that TFB’s weights are not honest, because TFI is a function of the Y i Y_{i} through β ^ 0 \hat{\beta}_{0} (and V ^ β 0 \hat{V}_{\beta_{0}} ). This is in contrast with many seminal methods in the weighting literature (e.g., Hainmueller, 2012 ; Imai and Ratkovic, 2014 ; Zubizarreta, 2015 ). However, dissecting TFB’s objective function is illustrative for envisioning its strengths, which all stem from consulting the outcomes. The | imbal ​ ( w , X , D ) ⊤ ​ β ^ 0 | |\mathrm{imbal}(w,X,D)^{\top}\hat{\beta}_{0}| term penalizes imbalance in f ^ 0 ​ ( X i ) = X i ⊤ ​ β ^ 0 \hat{f}_{0}(X_{i})=X_{i}^{\top}\hat{\beta}_{0} , which equals the EWC Bias if f 0 = f ^ 0 f_{0}=\hat{f}_{0} . However, even if f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} , it is unlikely that β ^ 0 = β 0 \hat{\beta}_{0}=\beta_{0} , so the Q q ​ ( 𝒳 P 2 ) × ‖ V ^ β 0 1 2 ​ imbal ​ ( w , X , D ) ‖ 2 \sqrt{Q_{q}(\mathcal{X}^{2}_{P})}\times||\hat{V}_{\beta_{0}}^{\frac{1}{2}}\mathrm{imbal}(w,X,D)||_{2} term penalizes imbalance in X i X_{i} , with the estimated variance of each β ^ 0 ( ℓ ) \hat{\beta}_{0}^{(\ell)} determining how to prioritize balance in the X i ( ℓ ) X_{i}^{(\ell)} . 5 5 5 Note that the coefficients’ covariance also plays a role, adding penalties and rewards for the signs of the leftover imbalances. To illustrate, let X i X_{i} be two-dimensional. Then, ‖ V ^ β 0 1 2 ​ imbal ​ ( w , X , D ) ‖ 2 \displaystyle||\hat{V}_{\beta_{0}}^{\frac{1}{2}}\mathrm{imbal}(w,X,D)||_{2} = ( var ^ ( β ^ 0 ( 1 ) ) [ imbal ( w , X ( 1 ) , D ) ] 2 + var ^ ( β ^ 0 ( 2 ) ) [ imbal ( w , X ( 2 ) , D ) ] 2 \displaystyle=\biggr(\widehat{\var}(\hat{\beta}_{0}^{(1)})[\mathrm{imbal}(w,X^{(1)},D)]^{2}+\widehat{\var}(\hat{\beta}_{0}^{(2)})[\mathrm{imbal}(w,X^{(2)},D)]^{2} OPEN + 2 ​ cov ^ ​ ( β ^ 0 ( 1 ) , β ^ 0 ( 2 ) ) ​ imbal ​ ( w , X ( 1 ) , D ) ​ imbal ​ ( w , X ( 2 ) , D ) ) 1 / 2 \displaystyle+2\widehat{\cov}(\hat{\beta}_{0}^{(1)},\hat{\beta}_{0}^{(2)})\mathrm{imbal}(w,X^{(1)},D)\mathrm{imbal}(w,X^{(2)},D)\biggr)^{1/2} Therefore, if cov ^ ​ ( β ^ 0 ( 1 ) , β ^ 0 ( 2 ) ) > 0 \widehat{\cov}(\hat{\beta}_{0}^{(1)},\hat{\beta}_{0}^{(2)})>0 , then the imbalances in the dimensions of X i X_{i} are penalized more if they are of the same sign, and less if they are of the opposite sign. If cov ^ ​ ( β ^ 0 ( 1 ) , β ^ 0 ( 2 ) ) < 0 \widehat{\cov}(\hat{\beta}_{0}^{(1)},\hat{\beta}_{0}^{(2)})<0 , then imbalances are penalized more if they are of the opposite sign, and less if they are of the same sign. This yields two desirable properties. First, TFB balances X i X_{i} to safeguard against uncertainty in β ^ 0 \hat{\beta}_{0} and only to a degree deemed necessary by its estimated variance. Section 4.3 also demonstrates that this, while simultaneously seeking balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) , can yield intentional imbalance in certain dimensions of X i X_{i} that offsets imbalance in others, granting efficiency gains without inviting bias. Second, the estimated variance of each β ^ 0 ( ℓ ) \hat{\beta}_{0}^{(\ell)} determines a hierarchy in balancing the X i ( ℓ ) X_{i}^{(\ell)} , meaning TFB incorporates variable selection. Section 4.3 shows how estimating β 0 \beta_{0} with sparsity (e.g., the LASSO) can exploit this. Finally, σ ^ 2 ​ ( 0 ) n c 2 ​ ‖ w ‖ 2 2 \frac{\hat{\sigma}^{2}(0)}{n_{c}^{2}}||w||_{2}^{2} controls the resulting estimator’s variance.

These qualities are not all unique to TFB. Prognostic score theory ( Hansen, 2008 ) also supports seeking balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) , inspiring some to incorporate f ^ 0 \hat{f}_{0} in propensity score matching schemes (e.g., Leacy and Stuart, 2014 ; Antonelli et al., 2018 ). Both Kuang et al., 2017 and Ning et al., 2020 emphasize balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) , and, along with Shortreed and Ertefaie, 2017 , develop methods that use f ^ 0 \hat{f}_{0} to inform variable selection, either in which dimensions of X i X_{i} to prioritize balance in, or which dimensions to use to estimate π \pi for propensity score weights. TFB’s contribution to this literature is its allowing V ^ β 0 \hat{V}_{\beta_{0}} to guide how to prioritize balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) over X i X_{i} , and in certain dimensions of X i X_{i} over others. Additionally, BAL1 and BAL2 could integrate TFB’s properties by carefully choosing δ \delta and ℱ \mathcal{F} , respectively — in fact, TFB is a special case of BAL2 where B ⁡ ( w ) = σ ^ 2 ​ ( 0 ) n c 2 ​ ‖ w ‖ 2 2 B(w)=\frac{\hat{\sigma}^{2}(0)}{n_{c}^{2}}||w||_{2}^{2} and ℱ = { x ⊤ ​ β | ‖ V ^ β 0 − 1 2 ​ ( β ^ 0 − β ) ‖ 2 ≤ Q q ​ ( 𝒳 P 2 ) } \mathcal{F}=\{x^{\top}\beta\ |\ ||\hat{V}_{\beta_{0}}^{-\frac{1}{2}}(\hat{\beta}_{0}-\beta)||_{2}\leq\sqrt{Q_{q}(\mathcal{X}^{2}_{P})}\} . In real-data scenarios, investigators could apply content knowledge to tune δ \delta and ℱ \mathcal{F} , potentially closing any performance gap between choosing arbitrary values and applying TFB. Nevertheless, TFB’s advantage is that it is defined by f ^ 0 \hat{f}_{0} and V ^ β 0 \hat{V}_{\beta_{0}} , turning the problem of how best to balance X i X_{i} into how best to model Y i ​ ( 0 ) Y_{i}(0) .

Lastly, using estimates of f d f_{d} in conjunction with weights, even honest ones, is not novel — it is essential for the “augmented (weighted) estimator”, the typical form of estimators that do so (e.g., Abadie and Imbens, 2011 ; Athey et al., 2018 ; Hirshberg and Wager, 2021 ). This includes “doubly-robust” estimators ( Robins et al., 1994 ; Robins and Rotnitzky, 1995 ; van der Laan and Rubin, 2006 ; Chernozhukov et al., 2018 ) which employ propensity score weights, and are consistent when f 0 f_{0} or π \pi has been correctly specified. 6 6 6 Tan, 2010 provides an illuminating review of doubly-robust estimators that can be expressed as τ ^ aug \hat{\tau}_{\mathrm{aug}} . Recall from Proposition 1 that the expectation of the EWC Bias is exactly the bias of τ ^ wdim \hat{\tau}_{\mathrm{wdim}} . Augmented estimators, τ ^ aug \hat{\tau}_{\mathrm{aug}} , bias-correct τ ^ wdim \hat{\tau}_{\mathrm{wdim}} by estimating the EWC Bias with a f ^ 0 \hat{f}_{0} , and subtracting the resulting estimate from τ ^ wdim \hat{\tau}_{\mathrm{wdim}} :

Noting that f ^ 0 ​ ( X i ) = X i ⊤ ​ β ^ 0 \hat{f}_{0}(X_{i})=X_{i}^{\top}\hat{\beta}_{0} in TFB reveals its connection to augmented estimators, as the estimated EWC Bias subtracted from τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) to form τ ^ aug ​ ( w , f ^ 0 ) \hat{\tau}_{\mathrm{aug}}(w,\hat{f}_{0}) is EWC Bias ^ = imbal ​ ( w , X , D ) ⊤ ​ β ^ 0 \widehat{\text{EWC Bias}}=\mathrm{imbal}(w,X,D)^{\top}\hat{\beta}_{0} , the magnitude of which TFB penalizes. Therefore, often, EWC Bias ^ ≈ 0 \widehat{\text{EWC Bias}}\approx 0 in TFB, implying τ ^ wdim ​ ( w ^ TFB ) ≈ τ ^ aug ​ ( w ^ TFB , f ^ 0 ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}_{\mathrm{TFB}})\approx\hat{\tau}_{\mathrm{aug}}(\hat{w}_{\mathrm{TFB}},\hat{f}_{0}) , as we find in our demonstrations below.

Although we have defined TFB in the context of regression functions that have linear representations, the extension of TFB to regression functions that do not have a linear representation (e.g., regression trees, or neural networks) is simple. Letting f ^ 0 ( X ) = [ f ^ 0 ( X 1 ) ⋯ f ^ 0 ( X n ) ] ⊤ \hat{f}_{0}(X)=[\hat{f}_{0}(X_{1})\ \cdots\ \hat{f}_{0}(X_{n})]^{\top} be the vector of predicted values from a general regression model, simply apply TFB with X = I n X=I_{n} (i.e., the n × n n\times n identity matrix), β ^ 0 = f ^ 0 ​ ( X ) \hat{\beta}_{0}=\hat{f}_{0}(X) , and V ^ β 0 \hat{V}_{\beta_{0}} set to V ^ f ^ 0 ​ ( X ) \hat{V}_{\hat{f}_{0}(X)} , an estimated variance of the prediction vector f ^ 0 ​ ( X ) \hat{f}_{0}(X) . Thus, while the linear form of TFB balances linear functions of X i X_{i} in the neighborhood of an estimated function that is parameterized by the coefficient vector β 0 \beta_{0} , this extended form of TFB instead balances prediction vectors in the neighborhood of a chosen f ^ 0 ​ ( X ) \hat{f}_{0}(X) .

A consequence of this extension is that TFB’s objective function is less intuitive at first glance because the scaled imbalance term, ‖ V ^ β 0 1 2 ​ imbal ​ ( w , X , D ) ‖ 2 ||\hat{V}_{\beta_{0}}^{\frac{1}{2}}\mathrm{imbal}(w,X,D)||_{2} , becomes ‖ V ^ f ^ 0 ​ ( X ) 1 2 ​ imbal ​ ( w , I n , D ) ‖ 2 ||\hat{V}_{\hat{f}_{0}(X)}^{\frac{1}{2}}\mathrm{imbal}(w,I_{n},D)||_{2} , and imbalance in I n I_{n} is less intuitive than imbalance in X i X_{i} . However, the scaling by V ^ f ^ 0 ​ ( X ) 1 2 \hat{V}_{\hat{f}_{0}(X)}^{\frac{1}{2}} gives this term an intuitive form in certain settings. For example, Appendix C.3 demonstrates that applying a generalized linear model results in TFB penalizing imbalance in functions of X i X_{i} in which f 0 f_{0} is assumed to be approximately linear, according to a first-order Taylor approximation.

As with any balancing method, the performance of linear TFB’s resulting estimator is highly dependent on whether or not f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} . Thus, the key risk with linear TFB is not choosing a X i X_{i} that contains the non-linear transformations of the original covariates required for f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} . Appendix C.4 demonstrates that bias can be a consequence of this. Therefore, although it provided motivation for TFI, TFB is not recommended when X i X_{i} is low-dimensional and OLS estimates f 0 f_{0} . 7 7 7 In fact, there is reason to believe that this form of TFB could perform worse than a method that solely seeks balance in X i X_{i} . This is because the term in TFB that penalizes imbalance in X i X_{i} , Q q ​ ( 𝒳 P 2 ) × ‖ V ^ β 0 1 2 ​ imbal ​ ( w , X , D ) ‖ 2 \sqrt{Q_{q}(\mathcal{X}^{2}_{P})}\times||\hat{V}_{\beta_{0}}^{\frac{1}{2}}\mathrm{imbal}(w,X,D)||_{2} , goes to 0 as n n increases quite generally, as V ^ β 0 ​ → 𝑝 ​ 0 \hat{V}_{\beta_{0}}\overset{p}{\rightarrow}0 under mild conditions (e.g., V ^ β 0 \hat{V}_{\beta_{0}} in ( 18 )). TFB would thus allow more imbalance in X i X_{i} as n n grows, assuming balance in f ^ 0 ​ ( X i ) = X i ⊤ ​ β ^ 0 \hat{f}_{0}(X_{i})=X_{i}^{\top}\hat{\beta}_{0} is sufficient. While this is a favorable result when f 0 f_{0} is linear in X i X_{i} , it could induce bias when f 0 f_{0} is not linear in X i X_{i} because balance in X i X_{i} could yield better balance in transformations of X i X_{i} that do contribute to f 0 f_{0} . Instead, we recommend the linear form of TFB when X i X_{i} is high-dimensional, either to start or because it is a high-dimensional transformation of a smaller set of variables, and a regularized regression estimates f 0 f_{0} . In these cases, f 0 ​ ( X i ) = X i ⊤ ​ β 0 f_{0}(X_{i})=X_{i}^{\top}\beta_{0} is believable, while balance in every dimension X i X_{i} is likely infeasible. But TFB will use f ^ 0 \hat{f}_{0} and its estimated variance to strategically leave imbalance X i X_{i} in a way that ideally yields a highly efficient estimator. Similarly, for the non-linear extension of TFB, we recommend applying machine learning regression methods that are flexible enough to capture a wide class of potential f 0 f_{0} .

These recommendations lead to the three forms of TFB that we primarily consider, and are listed in Table 1 , all of which apply regularized regressions or machine learning models. The first form is TFB-K, which applies kernel regularized least squares, setting X i = K i ​ c ⊤ X_{i}=K_{ic}^{\top} and β ^ 0 = α ^ 0 \hat{\beta}_{0}=\hat{\alpha}_{0} where

with λ \lambda chosen by cross-validation. 8 8 8 The krls function in R (from the KRLS package) is used to implement kernel regularized least squares, and employs leave-one-out cross validation for λ \lambda . Hainmueller and Hazlett, 2014 prove a suitable V ^ α 0 \hat{V}_{\alpha_{0}} is

Hainmueller and Hazlett, 2014 show that V ^ α 0 \hat{V}_{\alpha_{0}} is valid under the additional assumption that the ϵ i ​ ( 0 ) \epsilon_{i}(0) have constant variance given X i X_{i} . While this is unlikely, note that TFB-K does not require V ^ α 0 \hat{V}_{\alpha_{0}} for standard errors, but rather uses it to determine how to prioritize balance in f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) and K i ​ c K_{ic} versus the variance of the weights. Further, Appendix C.6 demonstrates that TFB-K can still perform well under heteroscedastic error. Therefore, we suspect that a violation to the constant variance assumption for ( 23 ) is not of major consequence.

The second form is TFB-L, which estimates f 0 f_{0} with LASSO regression, and obtains V ^ β 0 \hat{V}_{\beta_{0}} by residual bootstrapping. 9 9 9 The glmnet package in R is used to implement the LASSO. The λ \lambda needed for L 1 L_{1} regularization is found through cross-validation with the cv.glmnet function. When bootstrapping, we re-use the λ \lambda chosen from this cross-validation. Knight and Fu, 2000 and Chatterjee and Lahiri, 2010 prove the residual bootstrap is inconsistent under mild conditions for the LASSO’s asymptotic variance when one of more components of β 0 \beta_{0} are zero. However, if the residual bootstrap were to underestimate the variance of the corresponding coefficients, in the context of TFB-L, this may help the variable selection induced by the LASSO. Further, the residual bootstrap does not keep TFB-L from performing well in later demonstrations, so we forgo alternative methods (e.g., Chatterjee and Lahiri, 2011 ).

The third form is TFB-BART, which is an example of the non-linear extension of TFB, and estimates f 0 f_{0} with Bayesian Additive Regression Trees (BART; Hill, 2011 ). 10 10 10 The BART package in R is used to implement BART. We apply the gbart function with default parameters. In our experiments below, we regress all of the observed Y i Y_{i} on both X i X_{i} and D i D_{i} , and then obtain the f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) by making predictions with the resulting BART model at X i X_{i} and D i = 0 D_{i}=0 . TFB-BART sets the prediction vector f ^ 0 ​ ( X ) \hat{f}_{0}(X) to be the mean of the BART model’s posterior distribution for f ^ 0 ​ ( X ) \hat{f}_{0}(X) , and sets V ^ f ^ 0 ​ ( X ) \hat{V}_{\hat{f}_{0}(X)} to be the variance matrix of the posterior distribution for f ^ 0 ​ ( X ) \hat{f}_{0}(X) .


## 4.3 Demonstrations

This section demonstrates TFB’s merits in two data generating processes (DGPs), and in an application to the 2016 American Causal Inference Conference challenge data ( Dorie et al., 2019 ). For simplicity, key aspects of the DGPs (e.g., sample size, and overlap) are not varied here, but Appendices C.1 and C.2 examine TFB’s performance after varying these aspects. When relevant, we summarize the findings from these more expanded simulations.

To illustrate the benefits of TFB’s consulting the outcome, this first demonstration compares TFB-K and the honest kernel-based weights of Hazlett, 2020 and Kallus, 2020 , which balance K i K_{i} . By compromising between seeking balance in f 0 f_{0} through balance in f ^ 0 \hat{f}_{0} , and through balance in K i ​ c K_{ic} , TFB-K strategically leaves imbalances in certain confounders that offset imbalances in others, and achieves minimal bias and high efficiency. This is despite little overlap in some confounders, and approximating them with K i ​ c K_{ic} .

Consider a DGP in which X i X_{i} is drawn from a bivariate normal distribution around C i C_{i} , one of four equally likely (cluster) centers that are not known by the researcher,

Unknown to the researcher, however, D i D_{i} and Y i Y_{i} depend on the proximity of X i X_{i} to each center, given by Z i ( ℓ ) Z_{i}^{(\ell)} :

Each unit’s proximity to its own center then determines the probability of treatment:

where centering the Z i ( ℓ ) Z_{i}^{(\ell)} by 0.47 allows P ⁡ ( D i = 1 ) ≈ 0.50 P(D_{i}=1)\approx 0.50 , and units closer to their center are more likely to be treated. Figure 1 shows that units with centers c 2 c_{2} , c 3 c_{3} , and c 4 c_{4} show far more imbalance in the proximity to their center, and therefore their respective Z i ( ℓ ) Z_{i}^{(\ell)} , than are units with center c 1 c_{1} . Units with center c 1 c_{1} will thus be referred to as those in the “easy-to-balance” cluster, and the other units will be referred to as those in the “hard-to-balance” clusters.

Finally, the outcome is linear in the Z i ( ℓ ) Z_{i}^{(\ell)} ,

where the proximity to c 1 c_{1} , captured by Z i ( 1 ) Z_{i}^{(1)} , is by far the most important contributor to Y i Y_{i} , and there is no treatment effect (i.e., the ATT is 0). Note also that choice of var ⁡ ( ϵ i ) = 1.5 \var(\epsilon_{i})=1.5 results in a true R 2 = var ⁡ ( Y i − ϵ i ) var ⁡ ( Y i ) R^{2}=\frac{\var(Y_{i}-\epsilon_{i})}{\var(Y_{i})} of approximately 0.60.

Due to low overlap in the hard-to-balance clusters, balancing Z i ( 2 ) Z_{i}^{(2)} , Z i ( 3 ) Z_{i}^{(3)} , and Z i ( 4 ) Z_{i}^{(4)} would be challenging in finite samples even were they known to the researcher. However, balance in f 0 ​ ( X i ) f_{0}(X_{i}) is obtainable even without balance in Z i ( 2 ) Z_{i}^{(2)} , Z i ( 3 ) Z_{i}^{(3)} , and Z i ( 4 ) Z_{i}^{(4)} — inducing imbalance in Z i ( 1 ) Z_{i}^{(1)} of the opposite sign could offset imbalance in Z i ( 2 ) Z_{i}^{(2)} , Z i ( 3 ) Z_{i}^{(3)} , and Z i ( 4 ) Z_{i}^{(4)} . For example, weights such that imbal ⁡ ( w , Z ( 1 ) , D ) = − 1 100 \mathrm{imbal}(w,Z^{(1)},D)=-\frac{1}{100} and imbal ⁡ ( w , Z ( ℓ ) , D ) = 1 30 \mathrm{imbal}(w,Z^{(\ell)},D)=\frac{1}{30} for 2 ≤ ℓ ≤ 4 2\leq\ell\leq 4 achieve balance in f 0 ​ ( X i ) f_{0}(X_{i}) :

This involves reversing the sign of the original imbalance in Z i ( 1 ) Z_{i}^{(1)} , which is positive (see Figure 2(b) ). However, due to high overlap in the easy-to-balance cluster, this may require lower variance weights than it would require to achieve exact balance in all the Z i ( ℓ ) Z_{i}^{(\ell)} . Further, only slight imbalance in Z i ( 1 ) Z_{i}^{(1)} is needed due to the much larger influence of Z i ( 1 ) Z_{i}^{(1)} on Y i Y_{i} than that of the other Z i ( ℓ ) Z_{i}^{(\ell)} . Even though the Z i ( ℓ ) Z_{i}^{(\ell)} are unobserved in reality and TFB-K must approximate them with K i ​ c K_{ic} , TFB-K should in theory be able to discern this by consulting a f ^ 0 \hat{f}_{0} . Meanwhile, estimators that neglect Y i Y_{i} may increase their variance by balancing the hard-to-balance clusters and unimportant dimensions of K i K_{i} , or be too distracted by them to properly balance f 0 ​ ( X i ) f_{0}(X_{i}) .

Figure 2 confirms these hypotheses, comparing TFB-K to Kernel Balancing (KBAL; Hazlett, 2020 ) and Kernel Optimal Matching (KOM; Kallus, 2020 ), along with their augmented versions (augKBAL and augKOM). 11 11 11 KBAL exactly balances (via Entropy Balancing) an r r -dimensional approximation (i.e., using the first r r eigenvectors/eigenvalues) of the gram matrix, K K , choosing the r r that minimizes the worst-case EWC Bias. The kbal function in R (from the kbal package) is used to implement KBAL. KOM fits into the BAL2 framework where ℱ \mathcal{F} is a ball in a RKHS, and B ⁡ ( w ) = λ 2 ​ ‖ w ‖ 2 2 B(w)=\lambda^{2}||w||_{2}^{2} with a data-driven choice of λ \lambda , described in Kallus, 2020 . We code KOM in R from scratch, using MOSEK (through the Rmosek package in R ) to solve the BAL2 problem, and the optim function in R to find λ \lambda . f ^ 0 \hat{f}_{0} is found by kernel regularized least squares for augKBAL and augKOM. augKOM is a special case of the estimator studied by Hirshberg and Wager, 2021 . For each method, we use the Gaussian kernel, 𝒦 ( X i , X j ) = exp ( − | | X i − X j | | 2 2 / b ) \mathcal{K}(X_{i},X_{j})=\mathrm{exp}(-||X_{i}-X_{j}||_{2}^{2}/b) , with standardized X i X_{i} and we forgo a kernel-selection procedure, such as that proposed by Kallus, 2020 , for simplicity. Additionally, kernel regularized least squares with the Gaussian kernel and b = 2 b=2 performs well here ( f ^ 0 ​ ( X i ) \hat{f}_{0}(X_{i}) and f 0 ​ ( X i ) f_{0}(X_{i}) are correlated at 0.936 on average), and b = P b=P has been found to perform well empirically (e.g., Hainmueller and Hazlett, 2014 ; Schölkopf and Smola, 2002 ).

Define bias, root mean squared error (RMSE), and relative effective sample size (RESS) as

where m m indexes the iteration from 1 1 to M M , τ ^ wdim ​ ( w ^ ( m ) ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}^{(m)}) and w ^ i ( m ) \hat{w}^{(m)}_{i} are the estimate and weight for unit i i , respectively, from the m m th iteration, and n c ( m ) n_{c}^{(m)} is the size of the control group in the m m th iteration. In Figure 2(a) , TFB-K shows minimal bias, unlike KOM, and though KBAL also shows little bias, TFB-K’s RMSE is nearly two-thirds that of KBAL and KOM. Figure 2(b) reveals why this is — TFB-K leaves imbalance in Z i ( 1 ) Z_{i}^{(1)} of the opposite sign of the original imbalance to offset imbalance in the other Z i ( ℓ ) Z_{i}^{(\ell)} . Consequently, although KBAL obtains better balance in the Z i ( ℓ ) Z_{i}^{(\ell)} , its weights are higher variance than are TFB-K’s, as evidenced by TFB-K’s higher RESS (see Figure 2(a) ). Additionally, TFB-K outperforms augKBAL and augKOM here, although augKOM reduces the gap between KOM and TFB-K.

TFB-K’s strategy here notably challenges traditional advice that one’s weights should attain the best balance in X i X_{i} possible given the setting (e.g., Stuart, 2010 ). However, a more universal guiding principle is that, given equal bias, a more efficient estimator is preferable. Further, TFB should in general inhibit imbalances from becoming too extreme by using the variance of f ^ 0 \hat{f}_{0} to dictate how confidently it leaves imbalance. This is demonstrated in Figure 2(b) — balance is clearly a priority for TFB-K, as it successfully reduces the imbalance in each variable. Additionally, it obtains better balance in the Z i ( ℓ ) Z_{i}^{(\ell)} than does KOM because, tasked with minimal overlap in the hard-to-balance clusters, KOM instead prioritizes lower variance weights, as seen in its higher RESS. 12 12 12 Further discussion on KOM’s performance is warranted. Both TFB-K and KOM fit into the BAL2 framework with B ⁡ ( w ) = λ ​ ‖ w ‖ 2 2 B(w)=\lambda||w||_{2}^{2} for some λ \lambda , but differ on their choices of ℱ \mathcal{F} . Presented here for KOM are the results after using the data-driven procedure suggested by Kallus, 2020 to select λ \lambda . However, we have found that decreasing λ \lambda by several factors, giving KOM more freedom to increase the variance of its weights in order to further reduce the imbalance in the K i K_{i} , results in KOM performing on par with TFB-K in terms of bias and RMSE. Thus, TFB-K may only outperform KOM in the presented results because it happens to more effectively compromise imbalance reduction and variance in the specific DGP, rather than because it has chosen a ℱ \mathcal{F} that allows it to more effectively target balance in f 0 ​ ( X i ) f_{0}(X_{i}) , which is TFB-K’s central motivation.

Finally, recall that while key aspects of DGP 1 are not varied here for simplicity, Appendix C.1 examines how sensitive TFB’s performance is to varying these aspects. To summarize the results of this more expansive simulation, whether or not TFB-K leaves negative imbalance in Z i ( ℓ ) Z_{i}^{(\ell)} at a given sample size is sensitive to (i) the R 2 R^{2} for the model and (ii) the level of overlap in Z i ( 1 ) Z_{i}^{(1)} . In particular, when the R 2 R^{2} is higher, TFB-K more confidently leaves imbalance in Z i ( 1 ) Z_{i}^{(1)} because f ^ 0 \hat{f}_{0} has lower variance. Further, with more overlap in Z i ( 1 ) Z_{i}^{(1)} , leaving negative imbalance in Z i ( 1 ) Z_{i}^{(1)} is a viable strategy because it does not require outlandishly high variance weights. Nevertheless, TFB-K still has lower RMSE than do the comparison methods in almost all settings tried.

Next, TFB can prioritize balance in the dimensions of X i X_{i} that are most influential on Y i Y_{i} by estimating f 0 f_{0} with sparsity. This section demonstrates this by applying TFB-L, which estimates f 0 f_{0} with LASSO regression, in a high-dimensional setting.

Consider a DGP in which X i X_{i} contains three types of variables: (i) “confounders”, Z i Z_{i} , that are related to both D i D_{i} and Y i Y_{i} ; (ii) “distractors”, A i A_{i} , that are related to D i D_{i} , and are difficult to balance, but are unrelated to Y i Y_{i} ; and (iii) “extraneous” variables, U i U_{i} , that are independent of both D i D_{i} and Y i Y_{i} . The outcome and the log odds of treatment are both linear in Z i = [ Z i ( 1 ) ⋯ Z i ( 4 ) ] Z_{i}=[Z_{i}^{(1)}\ \cdots\ Z_{i}^{(4)}] ,

where the Z i ( ℓ ) Z_{i}^{(\ell)} are equally imbalanced, and have varying levels of influence on Y i Y_{i} . Furthermore, the ATT is 0, and ϵ i ​ ∼ i ​ i ​ d ​ N ​ ( 0 , 9.21 2 ) \epsilon_{i}\overset{iid}{\sim}N(0,9.21^{2}) allows the true R 2 R^{2} to be approximately 0.50. The Z i Z_{i} , the distractors ( A i A_{i} ), and the extraneous variables ( U i U_{i} ) are then generated as

Balance in Z i Z_{i} is sufficient to unbiasedly estimate the ATT. However, A i A_{i} and U i U_{i} , particularly A i A_{i} which is significantly more imbalanced than is Z i Z_{i} , complicate balancing the entirety of X i X_{i} . However, TFB-L performs well by finding β ^ 0 \hat{\beta}_{0} by LASSO regression. Figure 3 compares TFB-L with BAL1 where the δ ( ℓ ) \delta^{(\ell)} are all equal, and its augmented form (augABAL1). 13 13 13 Specifically, BAL1 here is the method from Zubizarreta, 2015 with δ \delta implied by the approx.balance function in R (from the balanceHD package) with default parameters. We use the residualBalance.ate function (from the same package) to implement augBAL1, with the LASSO as the regression estimator. augBAL1 is a special case of the estimator studied by Athey et al., 2018 . Further, to make the task of balancing Z i Z_{i} more challenging for each method, TFB-L and BAL1 expand on X i X_{i} , additionally (and needlessly) seeking balance in its squares and pairwise interactions, a total of 209 variables. Figure 3 also includes TFB-K to further illustrate the effect of TFB-L’s estimating f 0 f_{0} with sparsity. 14 14 14 As in DGP 1, TFB-K uses the Gaussian kernel with bandwidth b = P = 19 b=P=19 .

TFB-L shows minimal bias, while BAL1 is more comparable to a difference in means. TFB-L also boasts a lower RMSE than BAL1 by over a factor of two, and a higher RESS. TFB-L outperforms augBAL1 too, though augBAL1 reduces the gap between BAL1 and TFB-L. TFB-K also performs well here, and is a marked improvement over BAL1 and augBAL1 in both bias and RMSE, but falls short of TFB-L. Note also that TFB-L’s strong performance here persists even after varying key aspects of DGP 2 (see Appendix C.2 ).

As in DGP 1, the leftover imbalance in Figure 3(b) reveals why TFB-L excels. Balancing the distractors in A i A_{i} keeps BAL1 from properly balancing Z i Z_{i} and reduces its RESS. Meanwhile, TFB-L largely disregards balance in A i A_{i} , and obtains good balance in the Z i Z_{i} , particularly in Z i ( 1 ) Z_{i}^{(1)} , the most influential variable on Y i Y_{i} . This is a byproduct of how TFB-L models f 0 f_{0} — LASSO regression forces coefficients in β ^ 0 \hat{\beta}_{0} to 0 when their respective variables are weakly correlated with Y i Y_{i} , deflating their variances. Accordingly, Figure 4 shows that the distractors’, extraneous variables’, and polynomial terms’ diagonal elements in V ^ β 0 \hat{V}_{\beta_{0}} are small, illuminating why TFB-L devalues balance in those variables.

Additionally, the diagonal elements for the Z i ( ℓ ) Z_{i}^{(\ell)} in V ^ β 0 \hat{V}_{\beta_{0}} increase with the size of their coefficients in the model for Y i Y_{i} . Meanwhile, this variable selection does not carry over to TFB-K — it obtains balance on the distractors at almost the level of BAL1, while falling short of TFB-L’s balance in Z i ( 1 ) Z_{i}^{(1)} . This is because kernel regularized least squares does not estimate coefficients for K i ​ c K_{ic} with sparsity, so the diagonal entries of V ^ α 0 \hat{V}_{\alpha_{0}} , given by ( 23 ), depend more on the variance of the elements of K i ​ c K_{ic} than on their contribution to Y i Y_{i} . Nevertheless, TFB-K still obtains far better balance on Z i Z_{i} than does BAL1, which explains its improved performance.

Our final demonstration confirms TFB’s overall validity in a wide variety of settings by assessing TFB-BART’s and TFB-K’s performance on the data from the 2016 American Causal Inference Conference (ACIC) Challenge, “Is Your SATT Where It’s At?” ( Dorie et al., 2019 ). We find that TFB, with an appropriate choice of regression estimator, competes with some of the most highly regarded estimation approaches in the field.

In this ACIC challenge, various methods for estimating average treatment effects were applied to common simulated datasets, and the performance of these methods was compared. The data come from 77 distinct DGPs, each simulated 100 times (for a total of 7,700 datasets). 15 15 15 These data were accessed through the aciccomp GitHub repository. All DGPs use a common covariate matrix X X that is based on real data from the Collaborative Perinatal Project ( Niswander et al., 1972 ). But the DGPs vary in how the D i D_{i} and the Y i ​ ( d ) Y_{i}(d) are generated (from the X i X_{i} ), varying settings such as the functional forms of the conditional expectation functions of the potential outcomes and the propensity score, covariate overlap, treatment effect heterogeneity, and others (see Dorie et al., 2019 for more detail).

We apply TFB-BART and TFB-K to these datasets and, following Dorie et al., 2019 and Cousineau et al., 2023 , calculate their standardized bias and RMSE in relation to SATT:

where s s indexes the DGP, m m indexes the iteration, and σ ( y ) \sigma^{(y)} is the standard deviation of the Y i Y_{i} . Table 2(a) reports TFB-BART’s and TFB-K’s results, along with the results of the methods reported in Cousineau et al., 2023 , ordered by standardized RMSE. Table 2(a) also reports analogous results for an unweighted difference in means (DIM), and two g-computation ( Robins, 1986 ) estimators that impute the unobserved Y i ​ ( 0 ) Y_{i}(0) in SATT with predictions from a regression model: BART and KRLS. 16 16 16 For the KRLS and BART estimators, we use the same models that TFB-K and TFB-BART use. We also use sample splitting (see Section 4.5 ) with these estimators, using the same splits of the sample that the TFB estimators use. We do this so there is a more direct comparison between these g-computation estimators and the TFB estimators.

Dorie et al., 2019 note that non-parametric machine learning methods excel in these simulated datasets, particularly those that incorporate tree-based methods such as BART. Thus, it is affirming that TFB-BART is one of the top performers in Table 2(a) , reporting the third lowest RMSE (0.016) that is just barely higher than that of the top estimator (0.014). Additionally, TFB-BART slightly improves on the BART g-computation estimator — reducing the RMSE from 0.021 to 0.016.

Because tree-based methods excel in these datasets, it is unsurprising that TFB-K is not among of the top performers in Table 2(a) — in fact, all of the estimators with lower RMSE than TFB-K incorporate tree-based methods when modeling the outcome or the propensity score. More interesting is TFB-K’s performance relative to KBAL ( kbal ) and KRLS given the performance of linear_model , which reports the coefficient on D i D_{i} in a simple linear regression of Y i Y_{i} on X i X_{i} and D i D_{i} . TFB-K has meaningfully lower RMSE and bias than does KBAL, showing the benefits of consulting a model for the outcome to determine how to balance the high dimensional K i K_{i} . Further, TFB-K’s performance is impressive given the performance of KRLS, whose RMSE (0.108) resembles that of linear_model (0.135) far more than that of BART (0.021). In other words, TFB-K is only outperformed by methods that incorporate tree-based models, despite the outcome model it relies on not fitting these DGPs particularly well (as does BART). This shows the robustness that is gained from TFB-K’s seeking overall balance on K i K_{i} to prevent an overreliance on its outcome model.


## 4.4 Choosing q q

It is now worthwhile to examine q q , the probability threshold in TFB. Note that q q influences TFB’s weights through the constant Q q ​ ( 𝒳 P 2 ) Q_{q}(\mathcal{X}^{2}_{P}) in ( 19 ). Thus, when q q is closer to 1, TFB prioritizes reducing the imbalance in X i X_{i} , which could yield less bias but a higher variance estimator. When q q is closer to 0, reducing imbalance becomes less important, and lowering the variance of the weights is more important. Thus q q presents a bias-variance trade-off. Nevertheless, we recommend q = 0.95 q=0.95 generally, and this is used in all demonstrations here.

To justify this recommendation, we consider two scenarios that deserve separate discussions: (i) when P → ∞ P\rightarrow\infty as n → ∞ n\rightarrow\infty and (ii) when P P is fixed. Starting with the first scenario, notice that this applies to TFB-K, which replaces X i X_{i} with K i ​ c K_{ic} and thus P = n c P=n_{c} , and TFB-BART, which replaces X X with I n I_{n} and thus P = n P=n . This also applies to TFB-L in settings where one would add more non-linear transformations to X i X_{i} as n n grows. Note here that:

where Z ℓ Z_{\ell} are iid standard normal variables, Φ − 1 ​ ( q ) \Phi^{-1}(q) is the q q th quantile of a N ⁡ ( 0 , 1 ) N(0,1) , and P 2 ​ ( ∑ ℓ = 1 P Z ℓ 2 P − 1 ) ​ → 𝑑 ​ N ​ ( 0 , 1 ) \sqrt{\frac{P}{2}}(\frac{\sum_{\ell=1}^{P}Z_{\ell}^{2}}{P}-1)\overset{d}{\rightarrow}N(0,1) by the Central Limit Theorem. By ( 32 ) above, Q q 1 ​ ( 𝒳 P 2 ) Q q 2 ​ ( 𝒳 P 2 ) → 1 \frac{\sqrt{Q_{q_{1}}(\mathcal{X}^{2}_{P})}}{\sqrt{Q_{q_{2}}(\mathcal{X}^{2}_{P})}}\rightarrow 1 for fixed q 1 q_{1} and q 2 q_{2} and as P → ∞ P\rightarrow\infty , meaning that the specific choice of q q becomes inconsequential when n n , and thus P P , is large. Figure 5 shows this empirically — TFB-K’s bias and RMSE in DGP 1 become stable across q q as n n increases. However, with smaller n n , there is a bias-variance trade-off — bias decreases as q q increases, due to the higher emphasis on reducing imbalance in K i ​ c K_{ic} , but the RMSE is mostly unchanged, implying a higher variance esimator. See Appendices C.6 and C.7 , respectively, for similar findings for TFB-K in an extension to DGP 1 that has heteroscedastic error, and DGP 2.

Now consider the setting where P P is fixed. This is never the case for TFB-K or TFB-BART, but applies to TFB-L in cases where one would not expand X i X_{i} were the sample size to grow, and would like to take advantage of the LASSO’s variable selection. In this setting, V ^ β 0 ​ → 𝑝 ​ 0 \hat{V}_{\beta_{0}}\overset{p}{\rightarrow}0 quite generally, so TFB will devalue overall balance in X i X_{i} as n n grows. A q q near 1 may thus be preferable in this case because it will yield better balance on X i X_{i} , which may be valuable if f 0 f_{0} has been misspecified (i.e., is not linear in X i X_{i} ). Therefore, because q q appears to be inconsequential in the case where P → ∞ P\rightarrow\infty , and q q near 1 is advisable when P P is fixed, q = 0.95 q=0.95 seems a reasonable choice.


## 4.5 Sample splitting

To conclude the explication of TFB’s framework, we detail how to apply sample splitting to TFB, as in Chernozhukov et al., 2018 . Sample splitting was done in all demonstrations of TFB here.

Recall that the central motivation for TFB is to minimize (an approximation of) the EWC Bias. Further, Proposition 1 states that the bias of τ ^ wdim \hat{\tau}_{\mathrm{wdim}} is exactly the expectation of the EWC Bias. However, this result requires that each pair of w i w_{i} and Y i Y_{i} be independent of each other, given X X and D D . This is violated by TFB as defined, but is remedied by sample splitting.

Sample splitting with TFB requires randomly splitting the full sample into two non-overlapping (sub-)samples: Samples 1 and 2. Let the superscripts ( s ​ 1 ) (s1) and ( s ​ 2 ) (s2) denote values that come from Samples 1 and 2, respectively (e.g., OPEN w ^ TFB ( s ​ 1 ) ) \hat{w}_{\mathrm{TFB}}^{(s1)}) . First, use Sample 2 to obtain ( β ^ 0 ( s ​ 2 ) , V ^ β 0 ( s ​ 2 ) ) (\hat{\beta}^{(s2)}_{0},\hat{V}^{(s2)}_{\beta_{0}}) , and apply them to TFB in Sample 1 to form w ^ TFB ( s ​ 1 ) \hat{w}^{(s1)}_{\mathrm{TFB}} and τ ^ wdim ( s ​ 1 ) ​ ( w ^ TFB ( s ​ 1 ) ) \hat{\tau}_{\mathrm{wdim}}^{(s1)}(\hat{w}_{\mathrm{TFB}}^{(s1)}) . Next, switch the roles of the two sub-samples to obtain ( β ^ 0 ( s ​ 1 ) , V ^ β 0 ( s ​ 1 ) ) (\hat{\beta}^{(s1)}_{0},\hat{V}^{(s1)}_{\beta_{0}}) from Sample 1, and w ^ TFB ( s ​ 2 ) \hat{w}_{\mathrm{TFB}}^{(s2)} and τ ^ wdim ( s ​ 2 ) ​ ( w ^ TFB ( s ​ 2 ) ) \hat{\tau}_{\mathrm{wdim}}^{(s2)}(\hat{w}_{\mathrm{TFB}}^{(s2)}) from Sample 2. The final estimate is then the average of the estimates from each sub-sample:

Note that while TFB’s weights with sample splitting still depend on the observed outcomes, the weights in Sample 1 are independent of the outcomes in Sample 1 (given X X and D D ), and the weights in Sample 2 are independent of the outcomes in Sample 2 (given X X and D D ). Thus, each pair of w i w_{i} and Y i Y_{i} is independent of each other (given X X and D D ) as desired.

Finally, when sample-splitting in real-data applications, it is prudent to examine estimates from many random splits of the sample. However, if a single estimate is required for reporting, Chernozhukov et al., 2018 suggest the median. We demonstrate this procedure in Section 5 .


## 5 Application

This section assesses TFB’s performance on the National Supported Work (NSW) Demonstration data, accessible from Dehejia, 2023 . NSW was a labor training program in the mid-1970s that randomly selected its participants from a group of candidates. In addition to experimental treated and control groups drawn from the program candidates, data on comparison groups of non-candidates are available. LaLonde, 1986 and Dehejia and Wahba, 1999 use these data to compare non-experimental estimates of NSW’s impact on 1978 earnings (the outcome here) to the unbiased experimental estimate. Defining the treated (185 units), experimental control (260), and non-candidate comparison (2,490) groups as in Dehejia and Wahba, 1999 yields an experimental estimate of $1,794 and a naive observational estimate (i.e., the unweighted difference in means between the experimental treated and non-candidate comparison groups) of -$15,205.

The available covariates are age, years of education, an indicator of having a high school degree, 1974 and 1975 earnings, indicators of unemployment in 1974 and 1975, marital status, and several indicators of race/ethnicity. Figure 6 compares TFB-L, TFB-K, and TFB-BART to seven other estimators.

The first of these estimators is Entropy Balancing (EBAL; Hainmueller, 2012 ), which is an exact balancing method (see Section 3.2 ). The next three estimators are the same approximate balancing methods that were used in the demonstrations from Section 4.3 : BAL1 where all the δ ( ℓ ) \delta^{(\ell)} are equal (see Section 3.2 ), Kernel Balancing (KBAL; Hazlett, 2020 ), and Kernel Optimal Matching (KOM; Kallus, 2020 ). The final three estimators are augmented forms (see Section 4.2 ) of the three approximate balancing methods. 17 17 17 The ebalance function in R (from the ebal package) was used to implement EBAL. Each other method’s specifics are consistent with Sections 4.3 . The kernel-based approximate balancing methods (i.e., TFB-K, KBAL, and KOM) use the Gaussian kernel with bandwidth b = P = 10 b=P=10 , and their corresponding augmented forms use f ^ 0 \hat{f}_{0} from kernel regularized least squares. augABAL uses f ^ 0 \hat{f}_{0} from LASSO regression. TFB-K uses V ^ α 0 \hat{V}_{\alpha_{0}} from ( 23 ), TFB-L finds V ^ β 0 \hat{V}_{\beta_{0}} by residual bootstrapping, and TFB-BART uses the variance of its BART model’s posterior distribution for f ^ 0 ​ ( X ) \hat{f}_{0}(X) . All TFB estimates set q = 0.95 q=0.95 , per Section 4.4 . TFB-K, TFB-BART, EBAL, (aug)KBAL, and (aug)KOM are limited to the 10 untransformed covariates, while (aug)BAL1 and TFB-L additionally use the covariates’ squared terms and pairwise interactions, a total of 52 covariates. 18 18 18 Following Hainmueller, 2012 , we exclude various squares and interactions. These are the interaction between the indicator for high school degree and years of education, the interactions of the race/ethnicity indicators, and the squares and interactions of real earnings in 1974 and 1975. All TFB estimators employ sample splitting here (see Section 4.5 ), so estimates across 100 random splits of the sample are provided in Figure 6(b) , and Figure 6(a) reports the median estimate.

As are the other estimators, the TFB estimators are large improvements over the naive estimate of -$15,205. TFB-K is the closest to the experimental benchmark, and TFB-BART and TFB-L are the fifth and sixth closest (of ten). However, as this is just one realization of the data, drawing conclusions from these minute differences is challenging. It is more affirming that TFB performs comparably to other well-known estimators and that the experimental estimate falls within all of the TFB estimators’ 95% confidence intervals (as do the other estimators excluding augBAL1).

Finally, Table 3(a) reports the standardized imbalance in the covariates for each weighting method.

TFB shows similar tendencies here as in previous demonstrations. TFB estimators obtain very good balance on 1974 and 1975 earnings, which have the highest partial correlations with the outcome. Furthermore, because TFB-K does not estimate f 0 f_{0} with sparsity, TFB-K obtains good balance in all of the covariates, even those with low partial correlation with the outcome. Meanwhile, TFB-L and TFB-BART leave imbalance in age, the indicator of being Black, and the indicator of being married, the latter two of which show low partial correlation with the outcome.


## 6 Conclusion

This paper has introduced TFB, an approximate balancing framework that first regresses the outcome on the observed covariates, and then uses the resulting regression function and its estimated variance to determine how to balance the covariates. As a result, TFB seeks balance in the predicted values of the regression function and in the covariates, allowing the regression function’s variance to determine how much of the latter is necessary. In simulated examples, TFB showed promising results when compared to applications of existing approximate balancing methods that disregarded the outcome (i.e., are “honest”) and any potential background knowledge (e.g., which covariates are most influential on the outcome) when balancing the covariates. In real-data scenarios, investigators could apply background knowledge to tune these methods, potentially closing any performance gap that might exist between these methods and TFB. Nevertheless, TFB’s advantage is that the choice of regression estimator and an estimator for its variance entirely determines how it balances the covariates. This turns the problem of how best to balance the covariates into how best to model the outcome. TFB does, however, require different weights for different outcomes. This is a practical disadvantage in that it complicates analyses, and can be time-consuming. But it is also a potential advantage, particularly in settings with minimal overlap in the covariates — while it may be impossible to find a single set of weights that is appropriate for all outcomes, TFB may be able to find a different sets of weights that are individually appropriate for some (or all) of the outcomes.

One consequence of TFB is that it may intentionally leave imbalance in the covariates even when exact balance is feasible, either because certain dimensions appear conditionally unrelated to the outcome, or even to use imbalances in some dimensions to offset imbalances in others. Intentional imbalance is not a novel idea — several existing methods also leave imbalance in the name of variance reduction (e.g., Zubizarreta, 2015 ) or to prioritize balance in more predictive dimensions (e.g., Ning et al., 2020 ). However, the motivation behind this characteristic of TFB does challenge traditional advice (e.g., Stuart, 2010 ) that the ultimate goal of weighting is to equate the distributions of the covariates in the treated and control groups, with a particular focus on mean balance in the covariates as a benchmark for success. TFB instead argues that any balance in the covariates should only be a byproduct of balance in f 0 ​ ( X i ) = 𝔼 ⁡ [ Y i ​ ( 0 ) | X i ] f_{0}(X_{i})=\mathbbm{E}[Y_{i}(0)\ |\ X_{i}] , which is all that is required for unbiased estimation. It is understandable to be suspicious of this perspective in practice, given TFB’s reliance on a f ^ 0 \hat{f}_{0} , not f 0 f_{0} . However, note that it is theoretically sound, and is shown here to potentially yield efficiency gains. Further, recall that TFB still does value overall balance in the covariates, using it to safeguard against an over- reliance on f ^ 0 \hat{f}_{0} . Nevertheless, this presents a challenge from a diagnostics perspective, as in practice one can never know if imbalance that TFB leaves is cause for concern or if it can be safely ignored. However, note that in demonstrations here, TFB achieved good balance on the variables that were most influential on the outcome. Thus, in practice, we suggest first confirming that TFB has obtained good balance on the variables the researcher expects to be the most influential on the outcome, determined by content knowledge, or by calculating the partial correlations between each variable and the outcome. Then, one should confirm that the variables that TFB leaves more imbalance in are the variables that one expects to be less influential. Section 5 provides an example of this on real data.

As for implementation, TFB is recommended in high-dimensional settings, particularly the forms that use kernel regularized least squares to regress the outcome, an estimator that induces sparsity, such as the LASSO, or Bayesian Additive Regression Trees. However, we do not recommend a form of TFB that regresses the outcome with OLS in a low-dimensional setting. Furthermore, when applying TFB, a probability threshold ( q q ) close to 1 is recommended (e.g., q = 0.95 q=0.95 ). We also suggest performing sample splitting, calculating estimates across multiple random splits of the sample, and ultimately reporting the median. Note also that while this paper has framed TFB as an estimator for the average treatment effect on the treated (ATT), Appendix A adapts it to estimate the average treatment effect (ATE) and the average treatment effect on the controls (ATC). The R Package tfb implements TFB.

Finally, although this paper has demonstrated TFB’s merits in finite samples, proving its asymptotic properties would be a major future contribution. Appendix B , which proposes a variance estimator for TFB, discusses potential requirements for TFB to be asymptotically normal for a causal estimand of interest. In particular, the connection between TFB and “augmented minimax linear estimation” studied by Hirshberg and Wager, 2021 may be key. Ben-Michael et al., 2021a , which studies the asymptotic properties of balancing weight estimators, may also offer insights.


## References


## Appendix A Extensions to the ATC and the ATE

Although this paper describes TFI and TFB in the context of estimating the ATT, they are both easily extended to estimate the ATC and the ATE. This appendix details how to do so. Although it is a slight abuse of notation, let w ≥ 0 w\geq 0 be a general vector of nonnegative weights. In the context of the ATC, these weights will only be defined for treated units. In the context of the ATE, these weights will be defined for the full sample.


## A.1 Weighted difference in mean estimators for the ATC and the ATE

We first define the weighted difference in means estimators that will be used to estimate the ATC and the ATE.

A weighted difference in means estimator for the ATC takes the form

where all w i ≥ 0 w_{i}\geq 0 and, often, 1 n t ​ ∑ D i = 1 w i = 1 \frac{1}{n_{t}}\sum_{D_{i}=1}w_{i}=1 .

A weighted difference in means estimator for the ATE takes the form

where all w i ≥ 0 w_{i}\geq 0 and, often, 1 n c ​ ∑ D i = 0 w i = 1 \frac{1}{n_{c}}\sum_{D_{i}=0}w_{i}=1 and 1 n t ​ ∑ D i = 1 w i = 1 \frac{1}{n_{t}}\sum_{D_{i}=1}w_{i}=1 .


## A.2 TFI for the ATC and the ATE

This section extends TFI to weighted difference in means estimators of the ATC and the ATE. Like when estimating the ATT, these extensions of TFI are approximations of the bias of τ ^ wdim ( ATC ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATC})} and τ ^ wdim ( ATE ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATE})} in estimating the ATC and ATE, respectively.

First, however, we require extra notation. Define

where g g is an arbitrary vector-valued function. In words, imbal ( ATC ) ​ ( w , g ⁡ ( X ) , D ) \mathrm{imbal}^{(\mathrm{ATC})}(w,g(X),D) is the imbalance in g ⁡ ( X i ) g(X_{i}) between the unweighted control group and the weighted treated group. Then, define

In words, imbal ( ATE , d ) ​ ( w , g ⁡ ( X ) , D ) \mathrm{imbal}^{(\mathrm{ATE},d)}(w,g(X),D) is the imbalance in g ⁡ ( X i ) g(X_{i}) between the full sample and the weighted group with treatment status d ∈ { 0 , 1 } d\in\{0,1\} . Finally, let β ^ d \hat{\beta}_{d} for d ∈ { 0 , 1 } d\in\{0,1\} be the coefficients from regression estimators f ^ d ​ ( X i ) = X i ⊤ ​ β ^ d \hat{f}_{d}(X_{i})=X_{i}^{\top}\hat{\beta}_{d} , and let V ^ β ^ d \hat{V}_{\hat{\beta}_{d}} be estimates of their variances.

TFI for a τ ^ wdim ( ATC ) ​ ( w ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATC})}(w) is defined as

As before, q q is a probability threshold chosen by the researcher.

Define TFI for a τ ^ wdim ( ATE ) ​ ( w ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATE})}(w) as

Again, q q is a probability threshold chosen by the user.


## A.3 TFB for the ATC and the ATE

This section details how TFB finds weights to estimate the ATC and the ATE.

Similar to when estimating the ATT, TFB chooses weights to estimate the ATC that minimize the corresponding TFI subject to constraints on the weights’ variance. In other words,

where σ ^ 2 ( 1 ) = 1 n t ∑ i : D i = 1 ( Y i − X i ⊤ β ^ 1 ) 2 \hat{\sigma}^{2}(1)=\frac{1}{n_{t}}\sum_{i:D_{i}=1}(Y_{i}-X_{i}^{\top}\hat{\beta}_{1})^{2} .

To estimate the ATE, TFB chooses

where σ ^ 2 ( 0 ) = 1 n c ∑ i : D i = 0 ( Y i − X i ⊤ β ^ 0 ) 2 \hat{\sigma}^{2}(0)=\frac{1}{n_{c}}\sum_{i:D_{i}=0}(Y_{i}-X_{i}^{\top}\hat{\beta}_{0})^{2} and σ ^ 2 ( 1 ) = 1 n t ∑ i : D i = 1 ( Y i − X i ⊤ β ^ 1 ) 2 \hat{\sigma}^{2}(1)=\frac{1}{n_{t}}\sum_{i:D_{i}=1}(Y_{i}-X_{i}^{\top}\hat{\beta}_{1})^{2} .


## Appendix B Variance estimation and confidence intervals

Given that TFB’s weights are continuous, a bootstrap may be valid for variance estimation and confidence intervals. However, because high-dimensional regression estimators are recommended for TFB, the computation time required for a bootstrap may be impractical. This section thus proposes a closed-form estimated variance, and resulting confidence interval, for TFB. Asymptotic validity is not formally proven, but it is shown to perform well in DGPs 1 and 2 above.


## B.1 Variance estimation for the ATT

First, consider sufficient conditions for the asymptotic normality of τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) for general weights w ^ \hat{w} estimated from the data:

Given Assumption 1 , further assume the following conditions: (i) w ^ = w vec ​ ( X , D ) \hat{w}=w_{\mathrm{vec}}(X,D) for a function w vec ​ ( ⋅ ) w_{\mathrm{vec}}(\cdot) ; (ii) plim n → ∞ 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0)<\infty ; (iii) ∃ C ¯ , C ¯ > 0 \exists\underline{C},\overline{C}>0 such that C ¯ ≤ σ i 2 ​ ( 0 ) ≤ C ¯ \underline{C}\leq\sigma_{i}^{2}(0)\leq\overline{C} ; (iv) 𝔼 ⁡ ( [ Y i ​ ( 1 ) − f 0 ​ ( X i ) − ATT ] 2 | D i = 1 ) < ∞ \mathbbm{E}([Y_{i}(1)-f_{0}(X_{i})-\mathrm{ATT}]^{2}\ |\ D_{i}=1)<\infty ; (v) ∃ δ > 0 \exists\delta>0 such that

and (vi) EWC Bias = imbal ( w ^ , f 0 ( X ) , D ) = o p ( n − 1 / 2 ) \mathrm{EWC\ Bias}=\mathrm{imbal}(\hat{w},f_{0}(X),D)=o_{p}(n^{-1/2}) . Then, V ATT − 1 2 ​ ( w ^ ) ​ ( τ ^ wdim ​ ( w ^ ) − ATT ) ​ → 𝑑 ​ N ​ ( 0 , 1 ) V_{\mathrm{ATT}}^{-\frac{1}{2}}(\hat{w})(\hat{\tau}_{\mathrm{wdim}}(\hat{w})-\mathrm{ATT})\overset{d}{\rightarrow}N(0,1) where

Proof is given in Appendix D.3 . Condition (i) requires that w ^ i \hat{w}_{i} not depend on the Y i Y_{i} given X X and D D . Conditions (ii) and (v) then restrict how extreme the w ^ i \hat{w}_{i} can be in asymptopia. Conditions (iii) and (v) restrict the moments of ϵ i ​ ( 0 ) \epsilon_{i}(0) , and condition (iv) restricts the variance of the individual-specific treatment effects (i.e. 𝔼 ⁡ [ Y i ​ ( 1 ) − Y i ​ ( 0 ) | X i ] \mathbbm{E}[Y_{i}(1)-Y_{i}(0)\ |\ X_{i}] ). Finally, condition (vi) is key to the n \sqrt{n} -consistency of a τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) , requiring that the bias of τ ^ wdim ​ ( w ^ ) \hat{\tau}_{\mathrm{wdim}}(\hat{w}) converges in probability to 0 at a fast enough rate.

Note again that Proposition 3 does not specify the conditions under which TFB is asymptotically normal, but rather when a τ ^ wdim \hat{\tau}_{\mathrm{wdim}} with general weights is asymptotically normal. Nevertheless, it is worthwhile discussing conditions (i) and (vi) in the context of TFB. First, note that sample splitting allows condition (i) to hold for TFB individually within each of two splits of the sample. The proposed variance estimator leverages this fact, as will be detailed later.

Next, it should be emphasized that condition (vi) is far from trivial — for example, Abadie and Imbens, 2006 show it does not hold generally for the matching estimators they examine if P > 1 P>1 . However, there is precedent for balancing weights estimators, and particularly augmented estimators, satisfying this condition under additional assumptions (e.g., Athey et al., 2018 ; Hirshberg and Wager, 2021 ). In particular, that TFB is often approximately equal to an augmented estimator in practice reveals an relevant connection to the “augmented minimax linear estimator” explored by Hirshberg and Wager, 2021 . This class of estimator can be expressed as τ ^ aug \hat{\tau}_{\mathrm{aug}} with BAL2 weights with B ⁡ ( w ) ∝ ‖ w ‖ 2 2 B(w)\propto||w||_{2}^{2} and a general ℱ \mathcal{F} . 19 19 19 Hirshberg and Wager, 2021 describe ℱ \mathcal{F} as a function space that contains the difference between a f ^ 0 \hat{f}_{0} and f 0 f_{0} (i.e., f 0 − f ^ 0 f_{0}-\hat{f}_{0} ), rather than f 0 f_{0} itself. However, because ℱ \mathcal{F} is left general, this is ultimately only a difference in framing. Recall that TFB chooses BAL2 weights as well with B ⁡ ( w ) = σ ^ 2 ​ ( 0 ) n c 2 ​ ‖ w ‖ 2 2 B(w)=\frac{\hat{\sigma}^{2}(0)}{n_{c}^{2}}||w||_{2}^{2} and ℱ = { x ⊤ ​ β | ‖ V ^ β 0 − 1 2 ​ ( β ^ 0 − β ) ‖ 2 ≤ Q q ​ ( 𝒳 P 2 ) } \mathcal{F}=\{x^{\top}\beta\ |\ ||\hat{V}_{\beta_{0}}^{-\frac{1}{2}}(\hat{\beta}_{0}-\beta)||_{2}\leq\sqrt{Q_{q}(\mathcal{X}^{2}_{P})}\} . Thus, it seems plausible that TFB is asymptotically equivalent to an augmented minimax linear estimator with the same B ⁡ ( w ) B(w) and ℱ \mathcal{F} . This may imply asymptotic normality for TFB under assumptions similar to those proven in Hirshberg and Wager, 2021 , among them that f ^ 0 \hat{f}_{0} has several consistency properties for f 0 f_{0} . Hirshberg and Wager, 2021 also make assumptions on the function space ℱ \mathcal{F} for the BAL2 weights they examine. Thus, because V ^ β 0 \hat{V}_{\beta_{0}} (along with f ^ 0 \hat{f}_{0} ) determines the analogous ℱ \mathcal{F} for TFB, the properties of V ^ β 0 \hat{V}_{\beta_{0}} likely also play a role here. Further, although it does not appear that complete overlap in the conditional distributions of X i X_{i} (as in ( 13 )) is essential (see Appendix C.5 ), assurance that there exist weights that satisfy EWC in asymptopia would likely be required. Proving the exact assumptions needed for TFB to satisfy condition (vi), along with conditions (ii) and (v), is left to future work. Nevertheless, Proposition 3 , and Proposition 4 below, still suggest a closed-form variance estimator.

Turning back to general weights w ^ \hat{w} that are estimated from the data, assuming that f ^ 0 \hat{f}_{0} is a consistent estimator of f 0 f_{0} suggests the plug-in estimator for V ATT ​ ( w ^ ) V_{\mathrm{ATT}}(\hat{w}) ,

where e ^ i ​ ( 0 ) = Y i ​ ( 0 ) − f ^ 0 ​ ( X i ) \hat{e}_{i}(0)=Y_{i}(0)-\hat{f}_{0}(X_{i}) . Proposition 4 describes conditions under which V ^ ATT ​ ( w ^ , f ^ 0 ) ​ → 𝑝 ​ V ATT ​ ( w ^ ) \hat{V}_{\mathrm{ATT}}(\hat{w},\hat{f}_{0})\overset{p}{\rightarrow}V_{\mathrm{ATT}}(\hat{w}) .

Given Assumption 1 , and conditions (i)-(vi) for Proposition 3 , further assume that: (vii) 1 n ​ ∑ i = 1 n [ f 0 ​ ( X i ) − f ^ 0 ​ ( X i ) ] 2 = o p ​ ( 1 ) \frac{1}{n}\sum_{i=1}^{n}[f_{0}(X_{i})-\hat{f}_{0}(X_{i})]^{2}=o_{p}(1) ; (viii) 1 n c ∑ i : D i = 0 w ^ i 2 ϵ i 2 ( 0 ) → 𝑝 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\epsilon_{i}^{2}(0)\overset{p}{\rightarrow}\frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) ; and (ix) 1 n c ∑ i : D i = 0 w ^ i 2 [ f 0 ( X i ) − f ^ 0 ( X i ) ] 2 = o p ( 1 ) \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}[f_{0}(X_{i})-\hat{f}_{0}(X_{i})]^{2}=o_{p}(1) . Then, V ^ ATT ​ ( w ^ , f ^ 0 ) ​ → 𝑝 ​ V ATT ​ ( w ^ ) \hat{V}_{\mathrm{ATT}}(\hat{w},\hat{f}_{0})\overset{p}{\rightarrow}V_{\mathrm{ATT}}(\hat{w}) .

See Appendix D.4 for proof. Conditions (vii) and (ix) quantify how accurate an estimator of f 0 f_{0} that f ^ 0 \hat{f}_{0} must be in terms of unweighted and w ^ 2 \hat{w}^{2} -weighted mean squared error, respectively. Additionally, conditions (viii) and (ix) allow V ^ ATT ​ ( w ^ , f ^ 0 ) \hat{V}_{\mathrm{ATT}}(\hat{w},\hat{f}_{0}) to be robust to heteroscedastic ϵ i ​ ( 0 ) \epsilon_{i}(0) .

Propositions 3 and 4 suggest V ^ ATT ​ ( w ^ TFB , f ^ 0 ) \hat{V}_{\mathrm{ATT}}(\hat{w}_{\mathrm{TFB}},\hat{f}_{0}) as a variance estimator for TFB. However, TFB violates condition (i) from Proposition 3 as defined. Nevertheless, sample splitting corrects this. We first review sample splitting for TFB and its required notation from Section 4.5 . Sample splitting with TFB requires randomly splitting the full sample into two non-overlapping (sub-)samples: Samples 1 and 2. The superscripts ( s ​ 1 ) (s1) and ( s ​ 2 ) (s2) denote values that come from Samples 1 and 2, respectively. First, use Sample 2 to obtain ( β ^ 0 ( s ​ 2 ) , V ^ β 0 ( s ​ 2 ) ) (\hat{\beta}^{(s2)}_{0},\hat{V}^{(s2)}_{\beta_{0}}) , and apply them to TFB in Sample 1 to form w ^ TFB ( s ​ 1 ) \hat{w}^{(s1)}_{\mathrm{TFB}} and τ ^ wdim ( s ​ 1 ) ​ ( w ^ TFB ( s ​ 1 ) ) \hat{\tau}_{\mathrm{wdim}}^{(s1)}(\hat{w}_{\mathrm{TFB}}^{(s1)}) . Next, switch the roles of the two sub-samples to obtain ( β ^ 0 ( s ​ 1 ) , V ^ β 0 ( s ​ 1 ) ) (\hat{\beta}^{(s1)}_{0},\hat{V}^{(s1)}_{\beta_{0}}) from Sample 1, and w ^ TFB ( s ​ 2 ) \hat{w}_{\mathrm{TFB}}^{(s2)} and τ ^ wdim ( s ​ 2 ) ​ ( w ^ TFB ( s ​ 2 ) ) \hat{\tau}_{\mathrm{wdim}}^{(s2)}(\hat{w}_{\mathrm{TFB}}^{(s2)}) from Sample 2. The final estimate is then the average of the estimates from each sub-sample:

With sample splitting, condition (i) from Proposition 3 holds for the estimator from each sub-sample, with respective variances V ATT ( s ​ 1 ) ​ ( w ^ TFB ( s ​ 1 ) ) V_{\mathrm{ATT}}^{(s1)}(\hat{w}_{\mathrm{TFB}}^{(s1)}) and V ATT ( s ​ 2 ) ​ ( w ^ TFB ( s ​ 2 ) ) V_{\mathrm{ATT}}^{(s2)}(\hat{w}_{\mathrm{TFB}}^{(s2)}) . Then, following Proposition 4 , let V ^ ATT ( s ​ 1 ) ​ ( w ^ TFB ( s ​ 1 ) , f ^ 0 ( s ​ 2 ) ) \hat{V}_{\mathrm{ATT}}^{(s1)}(\hat{w}_{\mathrm{TFB}}^{(s1)},\hat{f}_{0}^{(s2)}) and V ^ ATT ( s ​ 2 ) ​ ( w ^ TFB ( s ​ 2 ) , f ^ 0 ( s ​ 1 ) ) \hat{V}_{\mathrm{ATT}}^{(s2)}(\hat{w}_{\mathrm{TFB}}^{(s2)},\hat{f}_{0}^{(s1)}) be the variance estimators from the two sub-samples. This leads to the proposed variance estimator:

( 100 × γ ) % (100\times\gamma)\% confidence intervals can then be obtained using the normal approximation: τ ^ wdim ( TFB ) ± Φ − 1 ​ ( 1 + γ 2 ) × var ^ ​ ( τ ^ wdim ( TFB ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{TFB})}\pm\Phi^{-1}(\frac{1+\gamma}{2})\times\sqrt{\widehat{\var}(\hat{\tau}_{\mathrm{wdim}}^{(\mathrm{TFB})})} . Figure 7 shows that 95% confidence intervals with the proposed variance estimator achieve essentially 95% coverage as n n increases. The undercoverage for TFB-K when n = 500 n=500 in DGP 1 is likely because TFB-K still shows bias at that sample size (see Figure 5 ). Note that in extensions to DGPs 1 and 2 in Appendices C.1 and C.2 that vary aspects of the DGPs (e.g., R 2 R^{2} , overlap, and sample size), the proposed confidence intervals reach, or fall just below, the target coverage rate of 95% when TFB’s bias is low.

Note that the asymptotic validity of var ^ ​ ( τ ^ wdim ( TFB ) ) \widehat{\var}(\hat{\tau}_{\mathrm{wdim}}^{(\mathrm{TFB})}) in ( 44 ) (given the other conditions from Propositions 3 and 4 ) requires that the estimates from each sub-sample are asymptotically uncorrelated. Proving this is left to future work, but Table 4 demonstrates that it is plausible, despite the estimates’ being correlated in finite samples (the Y i Y_{i} in Sample 1 contribute to w ^ TFB ( s ​ 2 ) \hat{w}_{\mathrm{TFB}}^{(s2)} from Sample 2, and vice versa). The correlation between the estimates appears to disappear as n n increases in DGPs 1 and 2.

Reporting the median estimate across many random splits of the sample, as suggested by Chernozhukov et al., 2018 , requires an adjusted variance. Again, let τ ^ wdim , s ( TFB ) \hat{\tau}_{\mathrm{wdim},s}^{(\mathrm{TFB})} be the TFB estimate from the s s th split of the sample, and let var ^ ​ ( τ ^ wdim , s ( TFB ) ) \widehat{\var}(\hat{\tau}_{\mathrm{wdim},s}^{(\mathrm{TFB})}) consistently estimate its variance. Results from Chernozhukov et al., 2018 imply the variance estimator for the median estimate, τ ^ wdim , med ( TFB ) \hat{\tau}_{\mathrm{wdim},\mathrm{med}}^{(\mathrm{TFB})} :

( 100 × γ ) (100\times\gamma) % confidence intervals can be obtained through the normal approximation: τ ^ wdim , med ( TFB ) ± Φ − 1 ​ ( 1 + γ 2 ) × var ^ ​ ( τ ^ wdim , med ( TFB ) ) \hat{\tau}_{\mathrm{wdim},\mathrm{med}}^{(\mathrm{TFB})}\pm\Phi^{-1}(\frac{1+\gamma}{2})\times\sqrt{\widehat{\var}(\hat{\tau}_{\mathrm{wdim},\mathrm{med}}^{(\mathrm{TFB})})} .


## B.2 Variance estimation for the ATC and the ATE

This section proposes variance estimators for TFB estimators of the ATC and ATE. Although it is a slight abuse of notation, let w ≥ 0 w\geq 0 be a general vector of nonnegative weights. In the context of the ATC, these weights will only be defined for treated units. In the context of the ATE, these weights will be defined for the full sample.

Proposition 5 describes sufficient conditions to determine the asymptotic normality of a τ ^ wdim ( ATC ) ​ ( w ^ ) \hat{\tau}^{(\mathrm{ATC})}_{\mathrm{wdim}}(\hat{w}) with general weights w ^ \hat{w} estimated from the data. Then, Proposition 6 introduces an estimator of the asymptotic variance of τ ^ wdim ( ATC ) ​ ( w ^ ) \hat{\tau}^{(\mathrm{ATC})}_{\mathrm{wdim}}(\hat{w}) and describes sufficient conditions for the estimator’s consistency.

Given Assumption 1 , further assume the following conditions: (i) w ^ = w vec ( ATC ) ​ ( X , D ) \hat{w}=w_{\mathrm{vec}}^{(\mathrm{ATC})}(X,D) for a function w vec ( ATC ) ​ ( ⋅ ) w_{\mathrm{vec}}^{(\mathrm{ATC})}(\cdot) ; (ii) plim n → ∞ 1 n t ∑ i : D i = 1 w ^ i 2 σ i 2 ( 1 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\sigma_{i}^{2}(1)<\infty ; (iii) ∃ C ¯ , C ¯ > 0 \exists\underline{C},\overline{C}>0 such that C ¯ ≤ σ i 2 ​ ( 1 ) ≤ C ¯ \underline{C}\leq\sigma_{i}^{2}(1)\leq\overline{C} ; (iv) 𝔼 ⁡ ( [ f 1 ​ ( X i ) − Y i ​ ( 0 ) − ATC ] 2 | D i = 0 ) < ∞ \mathbbm{E}([f_{1}(X_{i})-Y_{i}(0)-\mathrm{ATC}]^{2}\ |\ D_{i}=0)<\infty ; (v) ∃ δ > 0 \exists\delta>0 such that

and (vi) imbal ( ATC ) ( w ^ , f 1 ( X ) , D ) = o p ( n − 1 / 2 ) \mathrm{imbal}^{(\mathrm{ATC})}(\hat{w},f_{1}(X),D)=o_{p}(n^{-1/2}) . Then, V ATC − 1 2 ​ ( w ^ ) ​ ( τ ^ wdim ( ATC ) ​ ( w ^ ) − ATC ) → N ⁡ ( 0 , 1 ) V_{\mathrm{ATC}}^{-\frac{1}{2}}(\hat{w})(\hat{\tau}^{(\mathrm{ATC})}_{\mathrm{wdim}}(\hat{w})-\mathrm{ATC})\rightarrow N(0,1) where

Given Assumption 1 and conditions (i)-(vi) for Proposition 5 , further assume that: (vii) 1 n ​ ∑ i = 1 n [ f 1 ​ ( X i ) − f ^ 1 ​ ( X i ) ] 2 = o p ​ ( 1 ) \frac{1}{n}\sum_{i=1}^{n}[f_{1}(X_{i})-\hat{f}_{1}(X_{i})]^{2}=o_{p}(1) ; (viii) 1 n t ∑ i : D i = 1 w ^ i 2 ϵ i 2 ( 1 ) → 𝑝 1 n t ∑ i : D i = 1 w ^ i 2 σ i 2 ( 1 ) \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\epsilon_{i}^{2}(1)\overset{p}{\rightarrow}\frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\sigma_{i}^{2}(1) ; and (ix) 1 n t ∑ i : D i = 1 w ^ i 2 [ f 1 ( X i ) − f ^ 1 ( X i ) ] 2 = o p ( 1 ) \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}[f_{1}(X_{i})-\hat{f}_{1}(X_{i})]^{2}=o_{p}(1) . Then, V ^ ATC ​ ( w ^ , f ^ 1 ) ​ → 𝑝 ​ V ATC ​ ( w ^ ) \hat{V}_{\mathrm{ATC}}(\hat{w},\hat{f}_{1})\overset{p}{\rightarrow}V_{\mathrm{ATC}}(\hat{w}) where

The proofs for Propositions 5 and 6 are omitted here because the ATC is simply the negative of the ATT for the reversed treatment, D ~ i = 1 − D i \tilde{D}_{i}=1-D_{i} , and potential outcomes, Y ~ i ​ ( d ~ ) = Y i ​ ( 1 − d ~ ) \tilde{Y}_{i}(\tilde{d})=Y_{i}(1-\tilde{d}) (i.e., OPEN 𝔼 ⁡ [ Y i ​ ( 1 ) − Y i ​ ( 0 ) | D i = 0 ] = − 𝔼 ⁡ [ Y ~ i ​ ( 1 ) − Y ~ i ​ ( 0 ) | D ~ i = 1 ] ) \mathbbm{E}[Y_{i}(1)-Y_{i}(0)\ |\ D_{i}=0]=-\mathbbm{E}[\tilde{Y}_{i}(1)-\tilde{Y}_{i}(0)\ |\ \tilde{D}_{i}=1]) . Therefore, the proofs for Propositions 5 and 6 follow nearly identical steps to those for Propositions 3 and 4 (in Appendices D.3 and D.4 ), respectively.

We emphasize that Propositions 5 and 6 are for an estimator with general weights, not TFB specifically. However, as with the ATT, these propositions provide motivation for a closed-form variance estimator for TFB. We again propose sample splitting. First, randomly split the full sample into two non-overlapping (sub-)samples: Samples 1 and 2. Use Sample 2 to obtain ( β ^ 1 ( s ​ 2 ) , V ^ β 1 ( s ​ 2 ) ) (\hat{\beta}^{(s2)}_{1},\hat{V}^{(s2)}_{\beta_{1}}) , and apply them to TFB in Sample 1 to form w ^ TFB ( ATC ) , ( s ​ 1 ) \hat{w}^{(\mathrm{ATC}),(s1)}_{\mathrm{TFB}} and τ ^ wdim ( ATC ) , ( s ​ 1 ) ​ ( w ^ TFB ( ATC ) , ( s ​ 1 ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATC}),(s1)}(\hat{w}_{\mathrm{TFB}}^{(\mathrm{ATC}),(s1)}) . Next, switch the roles of the two sub-samples to obtain ( β ^ 1 ( s ​ 1 ) , V ^ β 1 ( s ​ 1 ) ) (\hat{\beta}_{1}^{(s1)},\hat{V}^{(s1)}_{\beta_{1}}) from Sample 1, and τ ^ wdim ( ATC ) , ( s ​ 2 ) ​ ( w ^ TFB ( ATC ) , ( s ​ 2 ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATC}),(s2)}(\hat{w}_{\mathrm{TFB}}^{(\mathrm{ATC}),(s2)}) from Sample 2. The final estimate is then average of the estimates from each sub-sample:

The proposed variance estimator is then:

( 100 × γ ) % (100\times\gamma)\% confidence intervals can then be obtained using the normal approximation: τ ^ wdim ( ATC ) , ( TFB ) ± Φ − 1 ​ ( 1 + γ 2 ) × var ^ ​ ( τ ^ wdim ( ATC ) , ( TFB ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATC}),(\mathrm{TFB})}\pm\Phi^{-1}(\frac{1+\gamma}{2})\times\sqrt{\widehat{\var}(\hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATC}),(\mathrm{TFB})})} .

Proposition 7 describes sufficient conditions to determine the asymptotic normality of a τ ^ wdim ( ATE ) ​ ( w ^ ) \hat{\tau}^{(\mathrm{ATE})}_{\mathrm{wdim}}(\hat{w}) with general weights w ^ \hat{w} estimated from the data. Then, Proposition 8 introduces an estimator of the asymptotic variance of τ ^ wdim ( ATE ) ​ ( w ^ ) \hat{\tau}^{(\mathrm{ATE})}_{\mathrm{wdim}}(\hat{w}) and describes sufficient conditions for the estimator’s consistency.

Given Assumption 1 , further assume the following conditions: (i) w ^ = w vec ( ATE ) ​ ( X , D ) \hat{w}=w_{\mathrm{vec}}^{(\mathrm{ATE})}(X,D) for a function w vec ( ATE ) ​ ( ⋅ ) w_{\mathrm{vec}}^{(\mathrm{ATE})}(\cdot) ; (ii) plim n → ∞ 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0)<\infty and plim n → ∞ 1 n t ∑ i : D i = 1 w ^ i 2 σ i 2 ( 1 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\sigma_{i}^{2}(1)<\infty ; (iii) ∃ C ¯ , C ¯ > 0 \exists\underline{C},\overline{C}>0 such that C ¯ ≤ σ i 2 ​ ( 0 ) ≤ C ¯ \underline{C}\leq\sigma_{i}^{2}(0)\leq\overline{C} and C ¯ ≤ σ i 2 ​ ( 1 ) ≤ C ¯ \underline{C}\leq\sigma_{i}^{2}(1)\leq\overline{C} ; (iv) 𝔼 ⁡ ( [ f 1 ​ ( X i ) − f 0 ​ ( X i ) − ATE ] 2 ) < ∞ \mathbbm{E}([f_{1}(X_{i})-f_{0}(X_{i})-\mathrm{ATE}]^{2})<\infty ; (v) ∃ δ > 0 \exists\delta>0 such that

and (vi) imbal ( ATE , 0 ) ( w ^ , f 0 ( X ) , D ) = o p ( n − 1 / 2 ) \mathrm{imbal}^{(\mathrm{ATE,0})}(\hat{w},f_{0}(X),D)=o_{p}(n^{-1/2}) and imbal ( ATE , 1 ) ( w ^ , f 1 ( X ) , D ) = o p ( n − 1 / 2 ) \mathrm{imbal}^{(\mathrm{ATE,1})}(\hat{w},f_{1}(X),D)=o_{p}(n^{-1/2}) . Then, V ATE − 1 2 ​ ( w ^ ) ​ ( τ ^ wdim ( ATE ) − ATE ) → N ⁡ ( 0 , 1 ) V_{\mathrm{ATE}}^{-\frac{1}{2}}(\hat{w})(\hat{\tau}^{(\mathrm{ATE})}_{\mathrm{wdim}}-\mathrm{ATE})\rightarrow N(0,1) where

Given Assumption 1 and conditions (i)-(vi) for Proposition 7 , further assume that: (vii) 1 n ​ ∑ i = 1 n [ f 0 ​ ( X i ) − f ^ 0 ​ ( X i ) ] 2 = o p ​ ( 1 ) \frac{1}{n}\sum_{i=1}^{n}[f_{0}(X_{i})-\hat{f}_{0}(X_{i})]^{2}=o_{p}(1) and 1 n ​ ∑ i = 1 n [ f 1 ​ ( X i ) − f ^ 1 ​ ( X i ) ] 2 = o p ​ ( 1 ) \frac{1}{n}\sum_{i=1}^{n}[f_{1}(X_{i})-\hat{f}_{1}(X_{i})]^{2}=o_{p}(1) ; (viii) 1 n c ∑ i : D i = 0 w ^ i 2 ϵ i 2 ( 0 ) → 𝑝 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\epsilon_{i}^{2}(0)\overset{p}{\rightarrow}\frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) and 1 n t ∑ i : D i = 1 w ^ i 2 ϵ i 2 ( 1 ) → 𝑝 1 n t ∑ i : D i = 1 w ^ i 2 σ i 2 ( 1 ) \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\epsilon_{i}^{2}(1)\overset{p}{\rightarrow}\frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\sigma_{i}^{2}(1) ; and (ix) 1 n c ∑ i : D i = 0 w ^ i 2 [ f 0 ( X i ) − f ^ 0 ( X i ) ] 2 = o p ( 1 ) \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}[f_{0}(X_{i})-\hat{f}_{0}(X_{i})]^{2}=o_{p}(1) and 1 n t ∑ i : D i = 1 w ^ i 2 [ f 1 ( X i ) − f ^ 1 ( X i ) ] 2 = o p ( 1 ) \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}[f_{1}(X_{i})-\hat{f}_{1}(X_{i})]^{2}=o_{p}(1) . Then, V ^ ATE ​ ( w ^ , f ^ 0 , f ^ 1 ) ​ → 𝑝 ​ V ATE ​ ( w ^ ) \hat{V}_{\mathrm{ATE}}(\hat{w},\hat{f}_{0},\hat{f}_{1})\overset{p}{\rightarrow}V_{\mathrm{ATE}}(\hat{w}) where

Proof for Proposition 7 is given in Appendix D.5 and proof for Proposition 8 is given in Appendix D.6 .

We emphasize that Propositions 7 and 8 are for an estimator with general weights, not TFB specifically. However, as with the ATT, these propositions provide motivation for a closed-form variance estimator for TFB. We again propose sample splitting. First, randomly split the full sample into two non-overlapping (sub-)samples: Samples 1 and 2. Use Sample 2 to obtain ( β ^ 0 ( s ​ 2 ) , V ^ β 0 ( s ​ 2 ) , β ^ 1 ( s ​ 2 ) , V ^ β 1 ( s ​ 2 ) ) (\hat{\beta}^{(s2)}_{0},\hat{V}^{(s2)}_{\beta_{0}},\hat{\beta}^{(s2)}_{1},\hat{V}^{(s2)}_{\beta_{1}}) , and apply them to TFB in Sample 1 to form w ^ TFB ( ATE ) , ( s ​ 1 ) \hat{w}^{(\mathrm{ATE}),(s1)}_{\mathrm{TFB}} and τ ^ wdim ( ATE ) , ( s ​ 1 ) ​ ( w ^ TFB ( ATE ) , ( s ​ 1 ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATE}),(s1)}(\hat{w}_{\mathrm{TFB}}^{(\mathrm{ATE}),(s1)}) . Next, switch the roles of the two sub-samples to obtain ( β ^ 0 ( s ​ 1 ) , V ^ β 0 ( s ​ 1 ) , β ^ 1 ( s ​ 1 ) , V ^ β 1 ( s ​ 1 ) ) (\hat{\beta}_{0}^{(s1)},\hat{V}^{(s1)}_{\beta_{0}},\hat{\beta}_{1}^{(s1)},\hat{V}^{(s1)}_{\beta_{1}}) from Sample 1, and τ ^ wdim ( ATE ) , ( s ​ 2 ) ​ ( w ^ TFB ( ATE ) , ( s ​ 2 ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATE}),(s2)}(\hat{w}_{\mathrm{TFB}}^{(\mathrm{ATE}),(s2)}) from Sample 2. The final estimate is then average of the estimates from each sub-sample:

The proposed variance estimator is then:

( 100 × γ ) % (100\times\gamma)\% confidence intervals can then be obtained using the normal approximation: τ ^ wdim ( ATE ) , ( TFB ) ± Φ − 1 ​ ( 1 + γ 2 ) × var ^ ​ ( τ ^ wdim ( ATE ) , ( TFB ) ) \hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATE}),(\mathrm{TFB})}\pm\Phi^{-1}(\frac{1+\gamma}{2})\times\sqrt{\widehat{\var}(\hat{\tau}_{\mathrm{wdim}}^{(\mathrm{ATE}),(\mathrm{TFB})})} .


## Appendix C Simulations


## C.1 Extension to DGP 1

This section investigates how TFB-K performs after varying important aspects of DGP 1 from Section 4.3 . As in DGP 1, X i X_{i} is drawn from a bivariate normal distribution around C i C_{i} , one of four equally likely (cluster) centers that are unknown to the researcher,

Though D i D_{i} and Y i Y_{i} again depend on Z i ( ℓ ) Z_{i}^{(\ell)} for ℓ = 1 , … , 4 \ell=1,\dots,4 ,

which are unknown to the researcher.

Several aspects of the probability of treatment and model for the outcome are varied. The probability of treatment is:

where ψ \psi , the coefficient on Z i ( 1 ) Z_{i}^{(1)} , takes values ψ ∈ ( 2 , 4 , 8 ) \psi\in(2,4,8) . ψ \psi controls the extent of overlap in the distributions of Z i ( 1 ) Z_{i}^{(1)} between the treated and control groups — ψ = 2 \psi=2 grants the most overlap, ψ = 8 \psi=8 grants the least overlap, and ψ = 4 \psi=4 grants medium overlap. The level of overlap for Z i ( 2 ) Z_{i}^{(2)} , Z i ( 3 ) Z_{i}^{(3)} , and Z i ( 4 ) Z_{i}^{(4)} is not varied here because the goal is to see if TFB still leaves imbalance in Z i ( 1 ) Z_{i}^{(1)} to overcome low overlap in the other Z i ( ℓ ) Z_{i}^{(\ell)} for different levels of overlap in Z i ( 1 ) Z_{i}^{(1)} .

The model for the outcome is:

where σ 2 \sigma^{2} , the variance of the error term ϵ i \epsilon_{i} , is varied so that the model R 2 = var ⁡ ( Y i − ϵ i ) var ⁡ ( Y i ) R^{2}=\frac{\var(Y_{i}-\epsilon_{i})}{\var(Y_{i})} takes values R 2 ∈ { 0.30 , 0.60 , 0.90 } R^{2}\in\{0.30,0.60,0.90\} in ( 53 ) The R 2 R^{2} is varied to see how the maximum predictive power of a f ^ 0 \hat{f}_{0} influences TFB-K’s performance. Finally, two sample sizes are tried: n ∈ { 500 , 1000 } . n\in\{500,1000\}. To summarize, the following aspects are varied:

ψ ∈ { 2 , 4 , 8 } \psi\in\{2,4,8\} in ( 52 )

R 2 ∈ { 0.30 , 0.60 , 0.90 } R^{2}\in\{0.30,0.60,0.90\}

n ∈ { 500 , 1000 } n\in\{500,1000\}

Note that ψ = 4 \psi=4 , R 2 = 0.60 R^{2}=0.60 and n = 1000 n=1000 essentially recreates DGP 1 in Section 4.3 .

As in Section 4.3 , TFB-K is compared to Kernel Balancing (KBAL; Hazlett, 2020 ) and Kernel Optimal Matching (KOM; Kallus, 2020 ). All methods are implemented in the same way as in Section 4.3 . Also included in the comparison are the augmented forms of KBAL (augKBAL) and KOM (augKOM), both using kernel regularized least squares as their regression function. Figure 8(g) reports the RMSE of each estimator, Figure 9(g) reports the bias, Figure 10(g) reports the median imbalance in Z i ( 1 ) Z_{i}^{(1)} , and Figure 11(g) reports the coverage rate of 95% confidence intervals found through the proposal in Section B across the 200 iterations from each setting.

Starting with RMSE in Figure 8(g) , as expected, the RMSE for each method tends to increase as overlap in Z i ( 1 ) Z_{i}^{(1)} decreases (i.e., ψ \psi increases), and RMSE tends to decrease as R 2 R^{2} and n n increase. The exceptions are KBAL and augKBAL, whose RMSEs are fairly consistent as n n and overlap change. In the vast majority of settings, TFB-K has the lowest RMSE. augKOM has the second lowest RMSE in the large majority of settings.

Figure 9(g) shows that TFB-K does not always have the least bias in every setting — KBAL tends to have the least bias, except when n = 1000 n=1000 with R 2 = 0.60 R^{2}=0.60 or 0.90 and high or medium overlap. Note also that the settings in which TFB-K shows little to no bias — when there is high or medium overlap combined with R 2 = 0.60 R^{2}=0.60 and n = 1000 n=1000 , or R 2 = 0.90 R^{2}=0.90 — are all settings in which TFB-K’s median imbalance for Z i ( 1 ) Z_{i}^{(1)} is negative (see Figure 10(g) ), i.e. the opposite sign of the original imbalance. Recall that in the original DGP 1 this allowed TFB-K to be nearly unbiased. That this occurs when the R 2 R^{2} is high and there is high or medium overlap makes sense. When the R 2 R^{2} is high, f ^ 0 \hat{f}_{0} is more predictive of the outcome and thus has lower variance, meaning TFB-K can more confidently leave imbalance in Z i ( 1 ) Z_{i}^{(1)} . Further, when there is high or medium overlap, leaving negative imbalance in Z i ( 1 ) Z_{i}^{(1)} does not require outlandishly high variance weights. Finally, Figure 11(g) shows that the proposed confidence intervals for TFB-K from Section B reach, or fall just below, the target coverage rate of 0.95 in the same settings in which TFB-K shows little bias (i.e., when when there is high or medium overlap combined with R 2 = 0.60 R^{2}=0.60 and n = 1000 n=1000 , or R 2 = 0.90 R^{2}=0.90 ).

In summary, TFB-K performs well even after varying important aspects of DGP 1 — it consistently has the lowest RMSE among the comparison methods tried. It also shows little bias when the model R 2 R^{2} is higher, and there is acceptable overlap in key confounders. When the model R 2 R^{2} and the overlap are lower, TFB-K appears to prioritize lower variance weights, leaving imbalance in confounders that induces bias. However, even in these settings, TFB-K often still has the lowest RMSE. Finally, the proposed confidence intervals from Section B perform well when TFB-K shows little bias.


## C.2 Extension to DGP 2

This section investigates how TFB performs after varying important aspects of DGP 2 from Section 4.3 . As in DGP 2, X i X_{i} contains three types of variables: (i) “confounders”, Z i Z_{i} , that are related to both D i D_{i} and Y i Y_{i} ; (ii) “distractors”, A i A_{i} , that are related to D i D_{i} , and are difficult to balance, but are unrelated to Y i Y_{i} ; and (iii) “extraneous” variables, U i U_{i} , that are independent of both D i D_{i} and Y i Y_{i} . The Z i Z_{i} are again generated as

and the log odds of treatment is again linear in Z i Z_{i} ,

Here, the R 2 R^{2} of the model for the outcome, and the dimensions of the distractor and extraneous variables are varied. First, the outcome is linear in Z i Z_{i} ,

where σ 2 \sigma^{2} , the variance of the error term ϵ i \epsilon_{i} , is varied so that the R 2 = var ⁡ ( Y i − ϵ i ) var ⁡ ( Y i ) R^{2}=\frac{\var(Y_{i}-\epsilon_{i})}{\var(Y_{i})} takes values R 2 ∈ { 0.20 , 0.50 , 0.80 } R^{2}\in\{0.20,0.50,0.80\} . The R 2 R^{2} is varied to examine how the maximum predictive power of a f ^ 0 \hat{f}_{0} influences TFB’s performance.

Then, the distractors ( A i A_{i} ) and the extraneous variables ( U i U_{i} ) are generated as

where k ∈ { 1 , 2 , 3 } k\in\{1,2,3\} . In other words, we consider settings with 5 5 distractors and 10 10 extraneous variables ( k = 1 k=1 ), 10 10 distractors and 20 20 extraneous variables ( k = 2 k=2 ), and 15 15 distractors and 30 30 extraneous variables ( k = 3 k=3 ). Finally, two samples sizes are tried: n ∈ { 500 , 1000 } . n\in\{500,1000\}. To summarize, the following aspects are varied:

R 2 ∈ { 0.20 , 0.50 , 0.80 } R^{2}\in\{0.20,0.50,0.80\} in ( 56 )

k ∈ { 1 , 2 , 3 } k\in\{1,2,3\} in ( 57 )

n ∈ { 500 , 1000 } n\in\{500,1000\}

Note that k = 1 k=1 , R 2 = 0.50 R^{2}=0.50 and n = 1000 n=1000 essentially recreates DGP 2 in Section 4.3 .

As in Section 4.3 , TFB-L and TFB-K are compared to an application of BAL1 that does not prioritize balance in any dimensions of X i X_{i} . All methods are implemented in the same way as in Section 4.3 . Note that for TFB-L and BAL1, this involves adding to X i X_{i} all its squares and pairwise interactions — when k = 1 k=1 (5 distractors and 10 extraneous variables) this totals 209 variables, when k = 2 k=2 (10 distractors and 20 extraneous variables) this totals 629 variables, and when k = 3 k=3 (15 distractors and 30 extraneous variables) this totals 1274 variables. Also included in the comparison is the augmented form of BAL1 (augBAL1), which uses the LASSO for its regression function. Figure 12(g) reports the RMSE of each estimator, Figure 13(g) reports the bias, and Figure 14(g) reports the coverage rate of 95% confidence intervals found through the proposal in Section B across 200 iterations from each setting.

Starting with RMSE in Figure 12(g) , TFB-L has the lowest RMSE in every setting. TFB-K has about the same, or a slightly higher, RMSE as does augBAL1 in most of the settings, except when R 2 = 0.20 R^{2}=0.20 and n = 500 n=500 . Figure 13(g) shows that TFB-L consistently has the lowest bias of all of the estimators tried here. However, TFB-L does show bias until R 2 = 0.80 R^{2}=0.80 . Further, TFB-K has the second lowest bias in most settings, though performs about the same as does augBAL1 when R 2 = 0.80 R^{2}=0.80 . Finally, Figure 14(g) shows that the proposed confidence intervals for TFB-L from Section B reach, or fall just below, the target coverage rate of 0.95 when TFB-L’s bias is lowest in Figure 13(g) (i.e., when R 2 = 0.50 R^{2}=0.50 and n = 1000 n=1000 , or when R 2 = 0.80 R^{2}=0.80 ).


## C.3 Applying generalized linear models with TFB

In this section, we consider applying a generalized linear model (GLM) to the non-linear extension of TFB. Assuming that f 0 f_{0} can be modeled as a GLM, we can write

where g g is the inverse link function of the GLM. We then estimate f 0 f_{0} as f ^ 0 ​ ( X i ) = g ⁡ ( X i ⊤ ​ β ^ 0 ) \hat{f}_{0}(X_{i})=g(X_{i}^{\top}\hat{\beta}_{0}) for some estimate β ^ 0 \hat{\beta}_{0} obtained through maximum likelihood estimation (MLE). Then let V ^ β ^ 0 \hat{V}_{\hat{\beta}_{0}} be a consistent estimator of the variance of β ^ 0 \hat{\beta}_{0} .

The non-linear extension of TFB requires a V ^ f ^ 0 ​ ( X ) \hat{V}_{\hat{f}_{0}(X)} . Because β ^ 0 \hat{\beta}_{0} is obtained through MLE, under the GLM model for f 0 f_{0} and iid data,

Applying the Delta Method with a general function h ⁡ ( ⋅ ) h(\cdot) then gives

Finally, letting h ( β 0 ) = f ^ 0 ( X ) = [ g ( X 1 ⊤ β ^ 0 ) ⋯ g ( X n ⊤ β ^ 0 ) ] ⊤ h(\beta_{0})=\hat{f}_{0}(X)=[g(X_{1}^{\top}\hat{\beta}_{0})\ \cdots\ g(X_{n}^{\top}\hat{\beta}_{0})]^{\top} to the above yields a plausible choice for V ^ f ^ 0 ​ ( X ) \hat{V}_{\hat{f}_{0}(X)} in the GLM setting:

Given this choice of V ^ f ^ 0 ​ ( X ) \hat{V}_{\hat{f}_{0}(X)} , the scaled imbalance term in the objective function for the non-linear extension of TFB becomes:

To summarize, this version of TFB seeks balance in g ′ ​ ( X i ⊤ ​ β ^ 0 ) ​ X i g^{\prime}(X_{i}^{\top}\hat{\beta}_{0})X_{i} . We can understand this choice by examining a first-order Taylor approximation of g ⁡ ( X i ⊤ ​ β 0 ) g(X_{i}^{\top}\beta_{0}) :

for some X ~ ∈ ℝ P \tilde{X}\in\mathbb{R}^{P} near X i X_{i} . Thus, f 0 f_{0} (under a GLM model) can be approximated as linear in g ′ ​ ( X ~ ⊤ ​ β 0 ) ​ X i g^{\prime}(\tilde{X}^{\top}\beta_{0})X_{i} . Since the Taylor approximation requires X ~ \tilde{X} to be near X i X_{i} , we may substitute X ~ \tilde{X} for X i X_{i} , further approximating f 0 f_{0} as a linear function of g ′ ​ ( X i ⊤ ​ β 0 ) ​ X i g^{\prime}(X_{i}^{\top}\beta_{0})X_{i} . Therefore, balance in g ′ ​ ( X i ⊤ ​ β ^ 0 ) ​ X i g^{\prime}(X_{i}^{\top}\hat{\beta}_{0})X_{i} should translate to balance in f 0 f_{0} when β ^ 0 \hat{\beta}_{0} is a good estimate of β 0 \beta_{0} , and g ′ ​ ( X i ⊤ ​ β ^ 0 ) ​ X i g^{\prime}(X_{i}^{\top}\hat{\beta}_{0})X_{i} is precisely what this GLM version of TFB seeks balance in, per ( 61 ).

To demonstrate, consider a DGP where P = 5 P=5 with X ( 5 ) = 1 X^{(5)}=1 being an intercept term, and each other dimension of X i X_{i} is simulated independently from a standard normal distribution:

Next, we generate the propensity scores according to a probit model,

where Φ ⁡ ( ⋅ ) \Phi(\cdot) is the CDF of the standard normal distribution. Finally, we generate Y i Y_{i} as a binary outcome variable that also comes from a probit model:

Note that X i ( 1 ) X_{i}^{(1)} is the most influential variable in determining Y i Y_{i} , and the ATT is 0.

We apply the non-linear extension of TFB with GLM probit regression as the regression estimator. Note in this setting that the link function g ⁡ ( ⋅ ) g(\cdot) is the standard normal CDF Φ ⁡ ( ⋅ ) \Phi(\cdot) , and

Thus, this application of TFB should seek balance in

where ϕ ⁡ ( ⋅ ) \phi(\cdot) is the probability density function of a standard normal random variable. Figure 15 reports how this application of TFB performs in 1000 iterations of this DGP with n = 1000 n=1000 , and investigates TFB’s average leftover imbalance in g ′ ​ ( X i ⊤ ​ β 0 ) ​ X i g^{\prime}(X_{i}^{\top}\beta_{0})X_{i} after weighting.

Because TFB here has correctly specified f 0 f_{0} , it is not surprising that the TFB estimator is effectively unbiased in Figure 15(a) . More interesting is how TFB chooses to leave imbalance in certain dimensions of g ′ ​ ( X i ⊤ ​ β 0 ) ​ X i g^{\prime}(X_{i}^{\top}\beta_{0})X_{i} , shown in Figure 15(b) . As does TFB-K in DGP 1, TFB here chooses to leave negative imbalances in g ′ ​ ( X i ⊤ ​ β 0 ) g^{\prime}(X_{i}^{\top}\beta_{0}) and g ′ ​ ( X i ⊤ ​ β 0 ) ​ X i ( 1 ) g^{\prime}(X_{i}^{\top}\beta_{0})X_{i}^{(1)} , which are of the opposite sign of the original imbalance in these components before weighting. TFB does this to counteract leftover imbalance g ′ ​ ( X i ⊤ ​ β 0 ) ​ X i ( ℓ ) g^{\prime}(X_{i}^{\top}\beta_{0})X_{i}^{(\ell)} for ℓ = \ell= 2, 3, and 4, because those components have a much higher starting imbalance than do the other dimensions of g ′ ​ ( X i ⊤ ​ β 0 ) ​ X i g^{\prime}(X_{i}^{\top}\beta_{0})X_{i} , and are thus harder to get good balance in.


## C.4 Danger of misspecifying f 0 f_{0} in TFB

In both DGPs 1 and 2 from Section 4.3 , the applications of TFB either correctly specify f 0 f_{0} or (in the case of TFB-K) f 0 f_{0} is well-approximated by a f ^ 0 \hat{f}_{0} from kernel regularized least squares. This section demonstrates the bias that can occur when TFB-L incorrectly specifies f 0 f_{0} .

An extension to DGP 2 is considered here. As in DGP 2, X i X_{i} contains three types of variables: (i) “confounders”, Z i Z_{i} , that are related to both D i D_{i} and Y i Y_{i} ; (ii) “distractors”, A i A_{i} , that are related to D i D_{i} , and are difficult to balance, but are unrelated to Y i Y_{i} ; and (iii) “extraneous” variables, U i U_{i} , that are independent of both D i D_{i} and Y i Y_{i} . The Z i Z_{i} , A i A_{i} , and U i U_{i} are again generated as

The difference from DGP 2 comes in the propensity store and model for the outcome. Instead of both the log odds of treatment and f 0 f_{0} being linear in Z i Z_{i} , the key transformation of Z i Z_{i} ,

is very influential in both models:

Centering ϕ ⁡ ( Z i ) \phi(Z_{i}) by 0.66 in the propensity score allows p ⁡ ( D i = 1 ) ≈ 0.50 p(D_{i}=1)\approx 0.50 , and choosing var ⁡ ( ϵ i ) = 20.7 2 \var(\epsilon_{i})=20.7^{2} allows the model R 2 = var ⁡ ( Y i − ϵ i ) var ⁡ ( Y i ) R^{2}=\frac{\var(Y_{i}-\epsilon_{i})}{\var(Y_{i})} to be approximately 0.50.

As in Section 4.3 , TFB-L is compared to an application of BAL1 that does not prioritize balance in any dimensions of X i X_{i} . Also included in the comparison is the augmented form of BAL1 (augBAL1), which uses the LASSO for its regression function. All methods are implemented in the same way as in Section 4.3 . Note that this involves adding to X i X_{i} all its squares and pairwise interactions, which totals 209 variables. However, this does not include ϕ ⁡ ( Z i ) \phi(Z_{i}) , meaning that all methods should expect bias. This bias is confirmed in Figure 16 — all methods, including TFB-L, show noticeable bias at n = 1000 n=1000 and n = 2000 n=2000 .


## C.5 Obviating complete overlap

Section 3.1 discusses how the traditional assumption of complete overlap in the conditional distributions of X i X_{i} , often written as ( 13 ), is not required for EWC . In fact all that is needed is for the average f 0 ​ ( X i ) f_{0}(X_{i}) in the treated group to be in the range of the f 0 ​ ( X i ) f_{0}(X_{i}) in the control group. For example, consider the following DGP:

Here this no overlap in the distribution of X i X_{i} — the control group only has values less than 0, and the treated group only has values greater than 0. Thus, both propensity score methods and any balancing method that requires exact balance on X i X_{i} would be impossible. However, 𝔼 ⁡ [ f 0 ​ ( X i ) | D i = 1 ] ≈ 0.45 \mathbbm{E}[f_{0}(X_{i})\ |\ D_{i}=1]\approx 0.45 , and the f 0 ​ ( X i ) f_{0}(X_{i}) among the control group have a range of ( 0.25 , ∞ ) (0.25,\infty) . Thus, EWC is often possible.

Consider now applying TFB to this DGP. Here, for simplicity, TFB will use an OLS that regresses Y i Y_{i} on ( X i , X i 2 ) (X_{i},X_{i}^{2}) to estimate f 0 f_{0} , and the sandwich variance estimator ( V ^ β 0 \hat{V}_{\beta_{0}} in ( 18 )). Figure 17 reports TFB’s performance in this DGP, and investigates the leftover imbalance in X i X_{i} and X i 2 X_{i}^{2} after weighting. Despite the lack of overlap in X i X_{i} , TFB is effectively unbiased at n = 2000 n=2000 . Per Figure 17(b) , TFB achieves this by inducing imbalance in X i 2 X_{i}^{2} to offset imbalance in X i X_{i} .

There are a couple things to note. First, note that even though OLS with a small number of regressors was applied here for TFB, I still do not recommend this practice in general. In this example, the OLS perfectly specifies f 0 f_{0} , which is unlikely in practice. However, despite this, it is still an important result that should have implications for the assumptions required for TFB’s asymptotic properties. It is clear that, depending on the consistency of the regression estimator f ^ 0 \hat{f}_{0} , one may only need a very weak overlap assumption in order for TFB to be asymptotically unbiased.


## C.6 Heteroscedastic error in DGP 1

This section considers an extension to DGP 1 from Section 4.3 in which the error in the model for Y i Y_{i} in ( 27 ) is heteroscedastic. Here, the X i X_{i} , Z i Z_{i} , and D i D_{i} are generated exactly as they are in DGP 1. However the model for Y i Y_{i} is now:

where the conditional variance of the ϵ i \epsilon_{i} is now a function of X i X_{i} . Furthermore, dividing f 0 ​ ( X i ) 2 f_{0}(X_{i})^{2} by 8 in the variance of ϵ i \epsilon_{i} results in a true R 2 = var ⁡ ( Y i − ϵ i ) var ⁡ ( Y i ) R^{2}=\frac{\var(Y_{i}-\epsilon_{i})}{\var(Y_{i})} of approximately 0.60, just like in the original DGP 1.

We consider the same estimators in this extension as the demonstrations on DGP 1 in Section 4.3 . The goal of this experiment is to see if TFB-K’s performance, which uses V ^ α ^ 0 \hat{V}_{\hat{\alpha}_{0}} in ( 23 ) as its variance estimator, is sensitive to heteroscedastic error. As mentioned previously, Hainmueller and Hazlett, 2014 show that V ^ α ^ 0 \hat{V}_{\hat{\alpha}_{0}} is valid only under homoscedastic error.

Figure 18 compares the estimators’ performance in this extension, and investigates the leftover imbalance in the Z i ( ℓ ) Z_{i}^{(\ell)} after weighting. As in Section 4.3 , TFB-K still has the lowest RMSE and shows little bias. Further, comparing Figure 18(b) to Figure 2(b) , we see that TFB-K shows similar tendencies in the original DGP 1 and this extension — it leaves imbalance in Z i ( 1 ) Z_{i}^{(1)} of the opposite sign to offset imbalance in the other Z i ( ℓ ) Z_{i}^{(\ell)} . Figure 19 then examines the bias and RMSE of TFB-K in this extension for varying q q . Comparing Figure 19 to Figure 5 , we again see very similar trends. With smaller n n , there a bias-variance trade-off in that the bias decreases as q q increases, but the RMSE is relatively stable. When n = 2000 n=2000 , both the bias and RMSE are quite stable across all values of q q .


## C.7 Performance of TFB-K in DGP 2 across different values of q q

Figure 20 reports the performance of TFB-K in DGP 2 across varying q q . At every sample size, TFB-K’s bias and RMSE are stable across all values of q q tried.


## Appendix D Proofs


## D.1 Proof of Proposition 1

Decomposing the difference between τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) and SATT reveals Proposition 1 :

First, SATT is unbiased for the ATT. Then, assuming that each pair of w i w_{i} and Y i ​ ( 0 ) Y_{i}(0) (and thus ϵ i ​ ( 0 ) \epsilon_{i}(0) ) are independent given X X and D D , taking the expectation of the both sides of ( 74 ) proves the result, as the terms with ϵ i ​ ( 0 ) \epsilon_{i}(0) are then mean-zero under Assumption 1 :

where the last line of ( D.1 ) above applies that 𝔼 ⁡ [ ϵ i ​ ( 0 ) | X ] = 𝔼 ⁡ [ ϵ i ​ ( 0 ) | X i ] = 0 \mathbbm{E}[\epsilon_{i}(0)\ |\ X]=\mathbbm{E}[\epsilon_{i}(0)\ |\ X_{i}]=0 by definition.

□ \square


## D.2 Proof of Proposition 2

Letting w i = w ⁡ ( X i , D i ) w_{i}=w(X_{i},D_{i}) for a weight function w ⁡ ( ⋅ ) w(\cdot) ,

Therefore, obtaining an unbiased estimate of the ATT using τ ^ wdim ​ ( w ) \hat{\tau}_{\mathrm{wdim}}(w) requires that

Applying the law of iterative expectations, ( 77 ) becomes

Assumption 1 then allows one to remove the conditioning on D i D_{i} in the inner expectations of both sides of ( 78 ), giving

Applying the definition of f 0 ​ ( X i ) = 𝔼 ⁡ [ Y i ​ ( 0 ) | X i ] f_{0}(X_{i})=\mathbbm{E}[Y_{i}(0)\ |\ X_{i}] to ( 79 ) yields WC .

□ \square


## D.3 Proof of Proposition 3

τ ^ wdim ​ ( w ^ ) − ATT \hat{\tau}_{\mathrm{wdim}}(\hat{w})-\mathrm{ATT} can be written as the sum of three terms that we analyze separately:

For ( a ) (a) , first notice that

where Assumption 1 allows the second line in ( D.3 ) above. Therefore,

Thus, the Central Limit Theorem applies to ( a ) (a) by ( D.3 ) and iid data, meaning that

where 𝔼 ⁡ ( [ Y i ​ ( 1 ) − f 0 ​ ( X i ) − ATT ] 2 | D i = 1 ) < ∞ \mathbbm{E}([Y_{i}(1)-f_{0}(X_{i})-\mathrm{ATT}]^{2}\ |\ D_{i}=1)<\infty by condition (iv) for the proposition. Some manipulation then gives that

Moving to ( b ) (b) , we first consider its distribution given X X and D D . To begin, under Assumption 1 , iid data, and condition (i) for the proposition,

Additionally, under conditions (iii) and (v) for the proposition, ∃ δ > 0 \exists\delta>0 such that

To see this, Assumption 1 , iid data, and conditions (i) and (iii) give

Then, by condition (v) for the proposition, ∃ δ , C ¯ δ > 0 \exists\delta,\overline{C}_{\delta}>0 that allow ( D.3 ) to continue as

Therefore, ( b ) (b) satisfies the Lyapunov condition conditional on X X and D D , meaning that, by the Lindeberg-Feller theorem,

which also implies here that

or, after some manipulation, that

where plim n → ∞ 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0)<\infty by condition (ii).

Putting these pieces together, n × ( a ) \sqrt{n}\times(a) and n × ( b ) \sqrt{n}\times(b) are asymptotically independent because they are independent given X X and D D and ( 89 ) holds given X X and D D . Therefore, by ( 80 ), ( 84 ), and ( 91 )

Further, n × EWC ​ Bias ​ → 𝑝 ​ 0 \sqrt{n}\times\mathrm{EWC\ Bias}\overset{p}{\rightarrow}0 by condition (vi) for the proposition. Thus, ( D.3 ) can be rewritten as

Finally, examining V ATT ​ ( w ^ ) V_{\mathrm{ATT}}(\hat{w}) , it is then evident that

Thus, applying ( D.3 ) to ( D.3 ) completes the proof.

□ \square


## D.4 Proof of Proposition 4

V ^ ATT ​ ( w ^ , f ^ 0 ) \hat{V}_{\mathrm{ATT}}(\hat{w},\hat{f}_{0}) can be rewritten as:

We prove the proposition by showing that ( a ) ​ → 𝑝 ​ 1 n t ​ 𝔼 ​ ( [ Y i ​ ( 1 ) − f 0 ​ ( X i ) − ATT ] 2 | D i = 1 ) (a)\overset{p}{\rightarrow}\frac{1}{n_{t}}\mathbbm{E}([Y_{i}(1)-f_{0}(X_{i})-\mathrm{ATT}]^{2}\ |\ D_{i}=1) and that ( b ) → 𝑝 1 n c 2 ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) (b)\overset{p}{\rightarrow}\frac{1}{n_{c}^{2}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) .

Starting with ( a ) (a) ,

Given iid data, and thus by the Law of Large Numbers,

where 𝔼 ⁡ ( [ Y i ​ ( 1 ) − f 0 ​ ( X i ) − ATT ] 2 | D i = 1 ) < ∞ \mathbbm{E}([Y_{i}(1)-f_{0}(X_{i})-\mathrm{ATT}]^{2}\ |\ D_{i}=1)<\infty by condition (iv) for Proposition 3 . By condition (vii) of the proposition,

and, by the Cauchy-Schwartz Inequality, along with ( 97 ) and ( 98 ),

Then, under the conditions for Proposition 3 , τ ^ wdim ​ ( w ^ ) ​ → 𝑝 ​ ATT \hat{\tau}_{\mathrm{wdim}}(\hat{w})\overset{p}{\rightarrow}\mathrm{ATT} , so

and, by iid data, and thus by the Law of Large Numbers,

Therefore, applying ( 97 ), ( 98 ), ( 99 ), ( 100 ), ( 101 ), and ( 102 ) to ( D.4 ) yields

Moving to ( b ) (b) in ( D.4 ),

By condition (viii) for the proposition,

Then, by condition (ix) for the proposition,

and using the Cauchy-Schwartz Inequality and ( 105 ),

Then, because plim n → ∞ 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) is finite by condition (ii) for Proposition 3 , we find that 1 n c 2 ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) \frac{1}{n_{c}^{2}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) in ( D.4 ) is O p ​ ( n − 1 ) O_{p}(n^{-1}) . Additionally using ( 106 ) allows ( D.4 ) to continue as

Therefore, applying ( 105 ), ( 106 ), and ( 108 ) to ( D.4 ) gives

Finally, applying ( 103 ) and ( 109 ) to ( D.4 ) completes the proof.

□ \square


## D.5 Proof of Proposition 7

τ ^ wdim ( ATE ) ​ ( w ^ ) − ATE \hat{\tau}^{(\mathrm{ATE})}_{\mathrm{wdim}}(\hat{w})-\mathrm{ATE} can be written as the sum of four terms that we analyze separately:

For ( a ) (a) , first notice that

Therefore,

Thus, the Central Limit Theorem applies to ( a ) (a) by ( D.5 ) and iid data, meaning that

where 𝔼 ⁡ ( [ f 1 ​ ( X i ) − f 0 ​ ( X i ) − ATE ] 2 ) < ∞ \mathbbm{E}([f_{1}(X_{i})-f_{0}(X_{i})-\mathrm{ATE}]^{2})<\infty by condition (iv) for the proposition.

As for ( b ) (b) and ( c ) (c) , we only thoroughly derive the asymptotic distribution of ( b ) (b) , because that of ( c ) (c) comes from a similar argument. We begin by considering the distribution of ( b ) (b) given X X and D D . Notice that under Assumption 1 , iid data, and condition (i) for the proposition,

Additionally, under conditions (iii) and (v) for the proposition, ∃ δ > 0 \exists\delta>0 such that

To see this, Assumption 1 , iid data, and conditions (i) and (iii) give

Then, by condition (v) for the proposition, ∃ δ , C ¯ δ > 0 \exists\delta,\overline{C}_{\delta}>0 that allow ( D.5 ) to continue as

Therefore, ( b ) (b) satisfies the Lyapunov condition conditional on X X and D D , meaning that, by the Lindeberg-Feller theorem,

which also implies here that

or, after some manipulation, that

where plim n → ∞ 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0)<\infty by condition (ii).

Moving to ( c ) (c) , the steps to derive its asymptotic distribution are nearly identical to those for ( b ) (b) , so we omit them here and simply state the final results. One finds that

which also means that

and, after some manipulation, that

where plim n → ∞ 1 n t ∑ i : D i = 1 w ^ i 2 σ i 2 ( 1 ) < ∞ \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{t}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\sigma_{i}^{2}(1)<\infty by condition (ii).

Putting these pieces together, n × ( a ) \sqrt{n}\times(a) , n × ( b ) \sqrt{n}\times(b) , and n × ( c ) \sqrt{n}\times(c) are asymptotically independent because they are independent given X X and D D and ( 118 ) and ( 121 ) both hold given X X and D D . Therefore, by ( D.5 ), ( 113 ), ( 120 ), and ( 123 )

Further, n × ( d ) ​ → 𝑝 ​ 0 \sqrt{n}\times(d)\overset{p}{\rightarrow}0 by condition (vi) for the proposition. Thus, ( D.5 ) can be rewritten as

Finally, examining V ATE ​ ( w ^ ) V_{\mathrm{ATE}}(\hat{w}) , it is then evident that

Thus, applying ( D.5 ) to ( D.5 ) completes the proof.

□ \square


## D.6 Proof of Proposition 8

V ^ ATE ​ ( w ^ , f ^ 0 ) \hat{V}_{\mathrm{ATE}}(\hat{w},\hat{f}_{0}) can be rewritten as:

We prove the proposition by showing that ( a ) ​ → 𝑝 ​ 1 n ​ 𝔼 ​ ( [ f 1 ​ ( X i ) − f 0 ​ ( X i ) − ATE ] 2 ) (a)\overset{p}{\rightarrow}\frac{1}{n}\mathbbm{E}([f_{1}(X_{i})-f_{0}(X_{i})-\mathrm{ATE}]^{2}) , ( b ) → 𝑝 1 n c 2 ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) (b)\overset{p}{\rightarrow}\frac{1}{n_{c}^{2}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) , and ( c ) → 𝑝 1 n t 2 ∑ i : D i = 1 w ^ i 2 σ i 2 ( 1 ) (c)\overset{p}{\rightarrow}\frac{1}{n_{t}^{2}}\sum_{i:D_{i}=1}\hat{w}_{i}^{2}\sigma_{i}^{2}(1) .

Starting with ( a ) (a) ,

Given iid data, and thus by the Law of Large Numbers,

where 𝔼 ⁡ ( [ f 1 ​ ( X i ) − f 0 ​ ( X i ) − ATE ] 2 ) \mathbbm{E}([f_{1}(X_{i})-f_{0}(X_{i})-\mathrm{ATE}]^{2}) is finite by condition (iv) for Proposition 7 . By condition (vii) of the proposition,

and, by the Cauchy-Schwartz Inequality, along with ( 129 ), ( 130 ), and ( 131 )

Then, under the conditions for Proposition 7 , τ ^ wdim ( ATE ) ​ ( w ^ ) ​ → 𝑝 ​ ATE \hat{\tau}^{(\mathrm{ATE})}_{\mathrm{wdim}}(\hat{w})\overset{p}{\rightarrow}\mathrm{ATE} , so

and, by iid data, and thus by the Law of Large Numbers,

Therefore, applying ( 129 ), ( 130 ), ( 131 ), ( D.6 ), ( 133 ), ( 134 ), ( 135 ), and ( 136 ) to ( D.6 ) yields

Moving to ( b ) (b) in ( D.6 ),

By condition (viii) for the proposition,

Then, by condition (ix) for the proposition,

and using the Cauchy-Schwartz Inequality and ( 139 ),

Then, because plim n → ∞ 1 n c ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) \underset{n\rightarrow\infty}{\mathrm{plim}}\ \frac{1}{n_{c}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) is finite by condition (ii) for Proposition 7 , we find that 1 n c 2 ∑ i : D i = 0 w ^ i 2 σ i 2 ( 0 ) \frac{1}{n_{c}^{2}}\sum_{i:D_{i}=0}\hat{w}_{i}^{2}\sigma_{i}^{2}(0) in ( D.6 ) is O p ​ ( n − 1 ) O_{p}(n^{-1}) . Additionally using ( 140 ) allows ( D.6 ) to continue as

Therefore, applying ( 139 ), ( 140 ), and ( 142 ) to ( D.6 ) gives

As for ( c ) (c) , deriving its probability limit follows nearly identical steps as does deriving the probability limit of ( b ) (b) . Therefore, we omit the derivation for ( c ) (c) and simply state the result. One finds that

Finally, applying ( 137 ), ( 143 ), and ( 144 ) to ( D.6 ) completes the proof.

□ \square

*