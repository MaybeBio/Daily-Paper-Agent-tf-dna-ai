## Time and space generalized diffusion equation on graph/networks

Normal and anomalous diffusion are ubiquitous in many complex systems Diffusive_Bunde_2018 . Here, we define a time and space generalized diffusion equation (GDE), which uses fractional-time derivatives and transformed d d -path Laplacian operators on graphs/networks. We find analytically the solution of this equation and prove that it covers the regimes of normal, sub- and superdiffusion as a function of the two parameters of the model. We extend the GDE to consider a system with temporal alternancy of normal and anomalous diffusion which can be observed for instance in the diffusion of proteins along a DNA chain. We perform computational experiments on a one-dimensional system emulating a linear DNA chain. It is shown that a subdiffusive-superdiffusive alternant regime allows the diffusive particle to explore more slowly small regions of the chain with a faster global exploration, than a subdiffusive-subdiffusive regime. Therefore, an alternancy of sliding (subdiffusive) with hopping and intersegmental transfer (superdiffusive) mechanisms show important advances for protein-DNA interactions.


## 1 Introduction

Diffusion–the net movement of particles in an environment, generally from a region of higher concentration to a region of lower concentration–is ubiquitous in natural and man-made systems. In the absence of obstacles to diffusion and traps, the diffusive particles describe a random walk motion on the environment, such that their mean squared displacements (MSD) scale linearly with time, ⟨ x 2 ⟩ ∝ t \langle x^{2}\rangle\propto t . This process is known as normal diffusion. However, the existence of obstacles in the environment may trigger long-jumps of the diffusive particle chen_mathematical_2020 ; king_non-local_2021 ; yu_single-molecule_2013 , such that the mean displacement of the particles is bigger than that of the normally diffusing ones in the same period of time, i.e., ⟨ x 2 ⟩ ∝ t γ > 1 \langle x^{2}\rangle\propto t^{\gamma>1} . This type of process is known as superdiffusive. On the other hand, it is possible that the environment has regions acting as traps for the particles, where they are retained for longer times than in a normal diffusive process. In this case, ⟨ x 2 ⟩ ∝ t γ < 1 , \langle x^{2}\rangle\propto t^{\gamma<1}, and the process is known as subdiffusive. From the modeling perspective there are several approaches to describe anomalous (sub- and super-) diffusion metzler_random_2000 ; sokolov2012models . From a physical perspective these processes have analogues in terms of anomalous heat conduction li2003anomalous , where normal diffusion implies normal heat conduction, superdiffusion implies anomalous heat conduction with a divergent thermal conductivity and subdiffusion implies anomalous heat conduction with a convergent thermal conductivity. In the last case the system is a thermal insulator in the thermodynamic limit.

It has been remarked that subdiffusion may arise as the result of the coexistence of time-periods dominated by normal transport with periods in which there is no effective transport. The last can emerge when the diffusive particle is temporarily trapped as a result of geometrical complexity and interactions with the environment. This could be clearly the case of the travel of contaminants in groundwater, which display much longer times than the ones expected from the classic diffusion. The motion of proteins while sliding on DNA during target search is believed to be subdiffusive in general kong2017rad4 . Simulations results for the case of T7 RNA polymerase promoter search on T7 DNA has been found to be subdiffusive for short times and asymptotically approaching normal diffusion barbi2004model . More recent intensive computational simulations also pointed out the important role of subdiffusive process in the diffusive search of proteins for their specific binding sites on DNA in the presence of the macromolecular crowding in cells liu2017facilitated . Nowadays it is well established that the molecular crowding of the internal cellular environment induces the emergence of anomalous subdiffusion of cytoplasmic macromolecules. This has been verified by means of fluorescence correlation spectroscopy and computer simulations weiss2004anomalous , fluorescence correlation spectroscopy banks2005anomalous , and by tracking fluorescently labeled mRNA molecules golding2006physical . The complexities of the process where studied with globular proteins dispersed in aqueous solution of poly(ethylene oxide) (PEO) to mimic a crowded environment. Using state-of-the-art neutron spin echo (NSE) and small-angle neutron scattering (SANS) techniques it was observed a fast dynamic corresponding to diffusion inside a trap built by the polymer mesh with slower process corresponding to the long time diffusion on macroscopic length scales gupta2016protein . It has also been found that water molecules jump randomly between trapping sites on protein surfaces, giving rise to subdiffusion. At longer times the subdiffusive exponent gradually increases towards normal diffusion due to a many-body volume-exclusion effect tan2018gradual .

The intermittency of fast and slow processes as the one described by the globular proteins in a crowded environment gupta2016protein can also be found in other scenarios. For instance, it has been reported that a proliferating, diffusing tumor within different surrounding tissue conditions migrates not only by using normal diffusion, but also using combinations of subdiffusion, superdiffusion, and even ballistic diffusion, with increasing mobility of the tumor cell when haptotaxis and chemotaxis toward the host tissue surrounding the proliferative tumor are involved jiang2014anomalous . The cytoskeleton (CSK), a crowded network of structural proteins that stabilizes cell shape and drives cell motions, displays spontaneous subdiffusive bead motions at short times followed by superdiffusive motion at longer times. The intermittency of the motions depended on both the approach to kinetic arrest and energy release due to ATP hydrolysis bursac2005cytoskeletal .

If we consider the protein’s diffusive transport on DNA in a wider perspective, i.e., not only considering the sliding process, then we observe a whole range of normal and anomalous behavior. Using recent advances in single molecule detection it has been observed that proteins diffusing along DNA follow different mechanisms, such as (i) random collision, (ii) sliding, (iii) hopping, (iv) intersegmental transfer and (v) active translocation shimamoto1999one ; gorman2008visualizing . While the sliding can give rise to subdiffusive and normal diffusion behavior, the hopping is known in other systems to produce superdiffusive behavior super_1 ; super_2 ; super_3 ; super_4 . Additionally, intersegmental transfers can transport a protein from one site in the DNA to another very distant from the original one inter_1 ; inter_2 ; inter_3 , which can give rise to superdiffusive behavior.

Many of the complex systems in which these normal and anomalous diffusion processes take place form interaction networks boccaletti_complex_2006 ; estrada_structure_2011 . For instance, DNA can be represented as a linear chain on which a protein is diffusing between its nodes and edges. Therefore, here we consider the time and space generalization of the diffusion equation on graphs/networks. We consider time-fractional derivatives, which account for nonlocality by time or dynamic memory tarasov2018no ; du2013measuring , and long-range jumps in the graph/network through the d d -path Laplacian operators estrada_path_2012 ; estrada_path_2017 ; estrada_path_2018 . We first define the generalized diffusion equation (GDE), study the main properties of its solution and find analytically the conditions for the existence of normal, sub- and superdiffusion. We also consider a time-varying GDE such that the three diffusive regimes appear intermittently with time. Finally, we apply this approach to the study of the diffusion of a particle through a linear chain representing a protein diffusing through DNA.


## 2 Preliminaries

Here we will use interchangeably the terms graph and network for G = ( V , E ) , G=(V,E), which in general will be connected and undirected. If the number of nodes n = # ​ V n=\#V is infinite we then assume that G G is locally finite (all vertices have finite degree). Furthermore, let l 2 ​ ( V ) l^{2}(V) be the Hilbert space of square-summable functions on V V .

We begin by defining the d d -path Laplacian operator on G G . Let d ​ i ​ s ​ t ​ ( v , w ) dist(v,w) be the length of the shortest path between v v and w w , and let k d ​ ( v ) k_{d}(v) be the d d -path degree of the vertex v v , defined by:

Let f f be a function acting over the set of vertices of G . G. Then, the d d -path Laplacian operator L d L_{d} is defined by:

Let e v ​ ( w ) e_{v}(w) be the orthonormal basis

Then, we have

The Mellin-transformed d d -path Laplacian is the following weighed sum of d d -path Laplacians:

where Δ \Delta is the diameter of the graph. This operator preserves several key properties of the graph Laplacian estrada_path_2012 ; estrada_path_2017 :

The Mellin-transformed d-path Laplacian is positive semidefinite. Furthermore, let k d , m ​ a ​ x := m ​ a ​ x ​ { k d ​ ( v ) : v ∈ V } k_{d,max}:=max\{k_{d}(v):v\in V\} . If k d , m ​ a ​ x ≤ C ​ k α k_{d,max}\leq Ck^{\alpha} , then L ~ ​ ( s ) \tilde{L}(s) is bounded for all s ∈ ℂ s\in\mathbb{C} with ℝ ⁡ ( s ) > α + 1 \mathbb{R}(s)>\alpha+1 .

When s → ∞ s\rightarrow\infty , all non-unity entries of L ~ ​ ( s ) \tilde{L}(s) vanish and we have the standard graph Laplacian operator L L . The physical difference of the d-path Laplacian operator with the fractional powers of the standard Laplacian have been analyzed in estrada_path_2021 . The standard diffusion equation on a graph is formulated on the basis of this operator as follows:

where 𝒟 \mathcal{D} is the diffusion coefficient, hereafter taken always to be unity. This equation has the well-known solution:

The function f ⁡ ( t ) f(t) can be interpreted as a probability density function (pdf) of the position of a hypothetical diffusing particle. Indeed, the diffusion equation ensures that several key properties of a pdf are satisfied: (i) If ( f 0 ) n ≥ 0 ​ ∀ n (f_{0})_{n}\geq 0\ \forall n , the exponential operator e − L ​ t e^{-Lt} ensures that the time evolved pdf remains positive: ( f ⁡ ( t ) ) n ≥ 0 ​ ∀ n , t (f(t))_{n}\geq 0\ \forall n,t . (ii) If the initial condition is normalized, ( ∑ n ( f 0 ) n = 1 \sum_{n}(f_{0})_{n}=1 ) then f ⁡ ( t ) f(t) remains normalized for any t t . This is because the diffusion equation preserves the 1-norm ∥ f ( t ) ∥ 1 := ∑ n f n ( t ) \parallel f(t)\parallel_{1}:=\sum_{n}f_{n}(t) :

where we have used L j ​ j = − ∑ i ≠ j L i ​ j L_{jj}=-\sum_{i\neq j}L_{ij} . The above equation implies that ∥ f i ∥ 1 ( t ) \parallel f_{i}\parallel_{1}(t) is constant, as previously stated. When the diffusion equation is defined as before, the mean square displacement (MSD) ⟨ x 2 ⟩ \langle x^{2}\rangle of the diffusive particle scales linearly with time: ⟨ x 2 ⟩ ∝ t \langle x^{2}\rangle\propto t , independently of the initial conditions and the diffusion coefficient. This is known as normal diffusion in the literature. However, many physical systems display the so-called anomalous diffusion metzler_random_2000 ; sokolov2012models , where the MSD scales as a power law with time: ⟨ x 2 ⟩ ∝ t γ \langle x^{2}\rangle\propto t^{\gamma} . If γ < 1 \gamma<1 , the system is in a subdiffusive regime, whereas if γ > 1 \gamma>1 , the system is in a superdiffusive regime. Moreover, in a normal diffusive regime the maximum of the probability density function (pdf), f m ​ a ​ x f_{max} , decreases as f m ​ a ​ x ​ ( t ) ∝ t − 0.5 f_{max}(t)\propto t^{-0.5} , while in superdiffusive and subdiffusive ones it decays as f m ​ a ​ x ​ ( t ) ∝ t − γ > 0.5 f_{max}(t)\propto t^{-\gamma>0.5} and f m ​ a ​ x ​ ( t ) ∝ t − γ < 0.5 f_{max}(t)\propto t^{-\gamma<0.5} , respectively. Similar decays exist also for the so-called Full Width at Half Maximum (FWHM) of the pdf, namely FWHM ∝ t γ > 0.5 \textrm{FWHM}\propto t^{\gamma>0.5} and FWHM ∝ t γ < 0.5 \textrm{FWHM}\propto t^{\gamma<0.5} for super- and subdiffusive regimes.


## 3 Time and space generalized diffusion on graphs/networks

Here we define a time and space generalized diffusion equation on graphs/networks in the following way. Let D t α D_{t}^{\alpha} be the Caputo fractional derivative and let L ~ ​ ( s ) \tilde{L}(s) be the Mellin-transformed d d -path Laplacian operator on G G . Then, the generalized diffusion equation (GDE) is defined as

where

f ′ ​ ( τ ) f^{\prime}(\tau) denotes the usual derivative. Here, 0 < α ≤ 1 0<\alpha\leq 1 and 0 < s < ∞ 0<s<\infty .

Obviously, when s → ∞ s\to\infty , we have D t α ​ f ​ ( t ) = − L ​ f ​ ( t ) , D_{t}^{\alpha}f(t)=-Lf(t), where L L is the standard graph Laplacian. This equation accounts for a time-fractional process only, without any spatial long-range jumps. On the other hand, when α = 1 \alpha=1 we get d ​ f ​ ( t ) d ​ t = − L ~ ​ ( s ) ​ f ​ ( t ) , \tfrac{df\left(t\right)}{dt}=-\tilde{L}(s)f(t), which accounts for long-range spatial jumps in the graph as studied previously in estrada_path_2017 .

Our first result is the general expression for the solution of the GDE defined before. We state this result in the following.

The solution of the GDE ( 3.1 ) is given by

where E α ​ ( … ) E_{\alpha}(...) is the Mittag-Leffler function of the corresponding matrix:

Let L ~ ​ ( s ) = U ​ Λ ​ U † \tilde{L}(s)=U\Lambda U^{\dagger} , where Λ = d ​ i ​ a ​ g ​ ( λ 1 , … , λ n ) \Lambda=diag(\lambda_{1},...,\lambda_{n}) and U U is a unitary matrix of eigenvectors of L ~ ​ ( s ) \tilde{L}(s) . The dagger symbol denotes the conjugate transpose. Thus:

Defining y ⁡ ( t ) = U † ​ f ​ ( t ) y(t)=U^{\dagger}f(t) , we obtain a set of decoupled fractional differential equations:

Let us use the Laplace transform of this fractional differential equation, and using the properties ℒ ​ { D t α ​ y } ​ ( u ) = u α ​ ℒ ​ { y } ​ ( u ) − u α − 1 ​ y ​ ( 0 ) \mathcal{L}\{D_{t}^{\alpha}y\}(u)=u^{\alpha}\mathcal{L}\{y\}(u)-u^{\alpha-1}y(0) as well as ℒ ⁡ { E α ​ ( − a ​ t α ) } ​ ( u ) = u α − 1 u α + a \mathcal{L}\{E_{\alpha}(-at^{\alpha})\}(u)=\frac{u^{\alpha-1}}{u^{\alpha}+a} , we find the solution:

Finally, we undo the change of basis y ⁡ ( t ) = U † ​ f ​ ( t ) y(t)=U^{\dagger}f(t) to obtain:

where the definition of a matrix function g g acting on a diagonalizable matrix A = U ​ Λ ​ U † A=U\Lambda U^{\dagger} is: g ⁡ ( A ) = U ​ g ​ ( Λ ) ​ U † g(A)=Ug(\Lambda)U^{\dagger} , and g ⁡ ( Λ ) := diag ​ ( g ⁡ ( λ i ) ) . g(\Lambda):=\textnormal{diag}(g(\lambda_{i})). ∎


## 3.1 Analysis of different diffusive regimes

We now focus on understanding how the GDE can give rise to different diffusive regimes in a given graph. In particular, we will focus here only in the one-dimensional case. For that, we will consider an infinite path graph, P ∞ P_{\infty} , which corresponds to the one-dimensional case. Anomalous diffusion in one-dimension has received much attention in the literature 1D_0 ; 1D_1 ; 1D_2 ; 1D_3 ; 1D_4 due to its practical relevance.

Let us start by defining the Fourier transform operator ℱ \mathcal{F} and its inverse ℱ − 1 \mathcal{F}^{-1} , respectively:

Let us first obtain the solution of the GDE for the P ∞ P_{\infty} graph.

The fundamental solution of the GDE for the infinite path graph P ∞ P_{\infty} and initial condition f n ​ ( 0 ) = f 0 = δ n ​ 0 f_{n}(0)=f_{0}=\delta_{n0} , can be expressed as:

with

where ζ ⁡ ( s ) = ∑ k = 1 ∞ 1 k s \zeta(s)=\sum_{k=1}^{\infty}\frac{1}{k^{s}} is the Riemann zeta function and Li s ​ ( x ) = ∑ n = 1 ∞ x n n s \textrm{Li}_{s}(x)=\sum_{n=1}^{\infty}\frac{x^{n}}{n^{s}} is the polylogarithm.

The Fourier transform of the Mellin-transformed d d -path Laplacian operator L ~ ​ ( s ) \tilde{L}(s) is estrada_path_2017 :

therefore:

Using the inverse Fourier transform and substituting the initial condition f n ​ ( 0 ) = ( f 0 ) n = δ n ​ 0 f_{n}(0)=(f_{0})_{n}=\delta_{n0} , we finally arrive at the expression:

∎

The time scaling of this expression is unclear, due to the polylogarithms inside the Mittag-Leffler function. However, to determine the diffusive regime that the system exhibits, it is sufficient to characterize the behavior of the solution in the limit of long times. Thus, we perform an asymptotic approximation, which is accounted for in the following result.

Let β > 0 \beta>0 and let l : [ − π , π ] → ℝ l:[-\pi,\pi]\to\mathbb{R} be a continuous function satisfying:

with some c > 0 c>0 . A ⁡ ( k ) ∼ B ⁡ ( k ) A(k)\sim B(k) denotes that lim k → 0 A ⁡ ( k ) B ⁡ ( k ) = 1 \lim_{k\to 0}\frac{A(k)}{B(k)}=1 . Then:

as t → ∞ t\to\infty .

Let ϵ > 0 \epsilon>0 and let us decompose the Fourier transform integral into:

Let us take the limit ϵ → 0 \epsilon\to 0 , so that the first integral becomes:

The second integral from ( 3.20 ) is negligible:

In particular, for a given ϵ \epsilon , the integral is negligible whenever t ≫ l ( ϵ ) − 1 / α t\gg l(\epsilon)^{-1/\alpha} . For identical reasons, the integral

is also negligible when t → ∞ t\to\infty . Thus, we can express the Fourier transform integral as:

∎

The solution of the GDE, when t → ∞ t\to\infty , is given by:

with

According to Theorem 6.5 of estrada_path_2017 , the function l s ​ ( k ) = 2 ​ ζ ​ ( s ) − Li s ​ ( e i ​ k ) − Li s ​ ( e − i ​ k ) l_{s}(k)=2\zeta(s)-\textrm{Li}_{s}(e^{ik})-\textrm{Li}_{s}(e^{-ik}) has the following asymptotics as k → 0 k\to 0 :

Moreover, l s ​ ( k ) l_{s}(k) is continuous and fulfills l s ​ ( k ) > 0 ​ ∀ k ≠ 0 , l s ​ ( 0 ) = 0 l_{s}(k)>0\ \forall k\neq 0,\ l_{s}(0)=0 ( estrada_path_2017 , Lemma 5.1). Thus, l s ​ ( k ) l_{s}(k) fulfills the hypotheses of Lemma 4 , so its asymptotic approximation is given by eq. ( 3.19 ). ∎

Equation ( 3.25 ) fully determines the solution of the GDE for long times. Unfortunately, the Fourier transform cannot be solved in terms of elementary functions. Nevertheless, the time scaling can be obtained with the following Theorem.

The solution of the GDE f ⁡ ( t ) f(t) has the asymptotic scaling with time f ⁡ ( t ) ∝ t − α β f(t)\propto t^{-\frac{\alpha}{\beta}} , as t → ∞ t\to\infty .

Let us exploit the parity of the integrand in eq. ( 3.25 ) and expand the cosine into a power series, we obtain:

We perform the change of variables u = c ​ k β ​ t α u=ck^{\beta}t^{\alpha} and split the integration interval into two:

The second integral is bounded by the constant e − π β ​ c ​ t α 2 e^{-\frac{\pi^{\beta}ct^{\alpha}}{2}} , as we will show now. For sufficiently big u u , E α ​ ( − u ) < e − u E_{\alpha}(-u)<e^{-u} and u 2 ​ j + 1 − β β < e u 2 u^{\frac{2j+1-\beta}{\beta}}<e^{\frac{u}{2}} , so:

In the limit t → ∞ t\to\infty , e − π β ​ c ​ t α 2 e^{-\frac{\pi^{\beta}ct^{\alpha}}{2}} approaches zero and thus the second integral from eq. ( 3.29 ) is negligible; therefore:

where I j ​ ( α , β ) = ∫ 0 ∞ d ​ u ​ u 2 ​ j + 1 − β β ​ E α ​ ( − u ) I_{j}(\alpha,\beta)=\int^{\infty}_{0}duu^{\frac{2j+1-\beta}{\beta}}E_{\alpha}(-u) . For large times and small m m (i.e., in the central region), the dominant term in the sum is the one with the smallest absolute value of the exponent of t t ; i.e., the term j = 0 j=0 . Hence, the asymptotic scaling with time is

∎

Additionally, let us find the scaling of two relevant observables: the height of the maximum of the pdf and the Full Width at Half Maximum (FWHM).

The maximum of the pdf, f m ​ a ​ x f_{max} , and FWHM fulfill the following asymptotic scaling laws in time: i) f m ​ a ​ x ​ ( t ) ∝ t − α β f_{max}(t)\propto t^{-\frac{\alpha}{\beta}} , ii) FWHM ​ ( t ) ∝ t α β \textrm{FWHM}(t)\propto t^{\frac{\alpha}{\beta}}

The proof of (i) is straightforward using eq. ( 3.31 ) for m = 0 m=0 :

To prove (ii), we make the rescaling m → m ​ t α β m\to mt^{\frac{\alpha}{\beta}} in eq. ( 3.25 ). The function f ⁡ ( m , t ) f(m,t) becomes:

where k ~ = t α β ​ k \tilde{k}=t^{\frac{\alpha}{\beta}}k . Let us apply this equation to find the scaling of the FWHM. Let ξ ⁡ ( t ) \xi(t) be the position at which the pdf reaches its Half Maximum at time t t (i.e., the ”Half Width at Half Maximum”), so that FWHM ​ ( t ) = 2 ​ ξ ​ ( t ) \textrm{FWHM}(t)=2\xi(t) . The FWHM can be determined through the equation f ⁡ ( ξ ⁡ ( t ) , t ) = f m ​ a ​ x ​ ( t ) 2 f(\xi(t),t)=\frac{f_{max}(t)}{2} . Using the time scaling of the maximum obtained in (i), we can express this as:

Comparing this equation with the scaling relation ( 3.34 ), it follows that ξ ⁡ ( t ) = ξ ⁡ ( 1 ) ​ t α β \xi(t)=\xi(1)t^{\frac{\alpha}{\beta}} , and thus:

∎

Remark: The MSD for processes with infinite variance of the step size distribution diverges jespersen_levy_1999 ; dybiec_levy_2017 , unless the step size distribution and the waiting time distribution are correlated klafter_stochastic_1987 . This is a well-known limitation of Levy flights and other stochastic processes that lead to superdiffusion dybiec_levy_2017 . Proposals of pseudo mean square displacements that remain finite for superdiffusive processes have been made jespersen_levy_1999 ; metzler_random_2000 , but their analytical calculation is far from trivial.

Let us now recall that for normal diffusion, the corresponding scaling laws are: i) f ⁡ ( t ) ∝ t − 1 2 f(t)\propto t^{-\frac{1}{2}} , ii) f m ​ a ​ x ​ ( t ) ∝ t − 1 2 f_{max}(t)\propto t^{-\frac{1}{2}} ,and iii) FWHM ​ ( t ) ∝ t 1 2 \textrm{FWHM}(t)\propto t^{\frac{1}{2}} . Let us focus here on the case 1 < s < 3 1<s<3 , where β = s − 1 \beta=s-1 . We find that the three scaling laws predict the same location of the three possible diffusive regimes:

Standard diffusion: α = s − 1 2 \alpha=\frac{s-1}{2} .

Superdiffusion: α > s − 1 2 \alpha>\frac{s-1}{2} .

Subdiffusion: α < s − 1 2 \alpha<\frac{s-1}{2} .

For s > 3 s>3 , β = 2 \beta=2 , which implies that subdiffusion happens for any α ∈ ( 0 , 1 ) \alpha\in(0,1) , and standard diffusion for α = 1 \alpha=1 . A phase diagram with the different diffusive regimes can be found in Figure 3.1 .


## 4 Time-dependent generalized diffusive processes

Let us consider here a system in which the different diffusive regimes alternate with time. That is, a system in which the diffusive particle behaves subdiffusively at a given time, then alternates with normal diffusion and superdiffusion as the time goes on. These processes can alternate cyclically as we will see later on this work.


## 4.1 Stepwise temporal dependence

The simplest way of achieving this is to let the parameter s s depend on time. This idea was previously explored by Allen-Perkins et al. allen-perkins_approach_2019 for the case of the d d -path Laplacian operator. Let us define:

We have the following generalized diffusion equation:

For a step-like s s like eq. ( 4.2 ), one can split the system into two time-independent equations:

with initial condition f A ​ ( 0 ) = f 0 f_{A}(0)=f_{0} . Then, expressing L ~ ​ ( s q ) \tilde{L}(s_{q}) ( q ∈ { A , B } ) (q\in\{A,B\}) as L ~ ​ ( s q ) = U q ​ Λ q ​ U q † \tilde{L}(s_{q})=U_{q}\Lambda_{q}U_{q}^{\dagger} , where U q U_{q} are unitary and Λ q = diag ​ ( ( λ q ) i ) \Lambda_{q}=\textnormal{diag}((\lambda_{q})_{i}) , and defining y q = U q † ​ f q y_{q}=U_{q}^{\dagger}f_{q} , we get a set of decoupled differential equations. The solution of each one is:

where C ~ q \tilde{C}_{q} are integration constants. C ~ A \tilde{C}_{A} can be obtained using the initial condition f A ​ ( 0 ) = f 0 f_{A}(0)=f_{0} and C ~ B \tilde{C}_{B} is found imposing the continuity of the function at t = t s ​ w t=t_{sw} : f A ​ ( t s ​ w ) = f B ​ ( t s ​ w ) f_{A}(t_{sw})=f_{B}(t_{sw}) . Undoing the change of basis induced by U q † U_{q}^{\dagger} , we obtain the following solution in terms of matrix functions:

From now on, we assume that t > t s ​ w t>t_{sw} . We express eq. ( 4.7 ) as:

where f 1 ​ ( t s ​ w , s 1 , s 2 ) = E α ​ ( − L ~ ​ ( s 2 ) ​ t s ​ w α ) − 1 ​ E α ​ ( − L ~ ​ ( s 1 ) ​ t s ​ w α ) ​ f 0 f_{1}(t_{sw};s_{1},s_{2})=E_{\alpha}(-\tilde{L}(s_{2})t_{sw}^{\alpha})^{-1}E_{\alpha}(-\tilde{L}(s_{1})t_{sw}^{\alpha})f_{0} . The introduction of f 1 f_{1} reduces the problem to a time-independent expression, analogous to eq. ( 3.9 ), but with a different initial condition. The time-evolved system is then

as t → ∞ t\to\infty , where we have used the asymptotic equivalence l s 2 ​ ( k ) ∼ c 2 ​ | k | β 2 l_{s_{2}}(k)\sim c_{2}|k|^{\beta_{2}} as k → 0 k\to 0 and Lemma 4 . The time scaling of the pdf can be calculated using the procedure from Theorem 6 , obtaining:

which confirms that the dominant time scaling is still t − α β 2 t^{-\frac{\alpha}{\beta_{2}}} . In other words, the phase diagram from the previous section remains unchanged: the system behaves asymptotically as if the Laplacian L ⁡ ( s 1 ) L(s_{1}) had never affected the dynamics.


## 4.2 Periodic temporal alternancy

Consider the following time-dependent parameter s s , with period T T :

where n ∈ ℕ ∪ { 0 } n\in\mathbb{N}\cup\{0\} . In order to obtain the full solution of the problem, let us define f ( n ) ​ ( t ) f^{(n)}(t) as the restriction of f ⁡ ( t ) f(t) to t ∈ [ n ​ T , ( n + 1 ) ​ T ) t\in[nT,(n+1)T) : f ( n ) ​ ( t ) = f ⁡ ( t ) | [ n ​ T , ( n + 1 ) ​ T ) f^{(n)}(t)=f(t)|_{[nT,(n+1)T)} . To solve the problem, it suffices to find an expression for f ( n ) ​ ( t ) f^{(n)}(t) for arbitrary n n .

The solution of the GDE with a periodic parameter s ⁡ ( t ) s(t) and initial condition f ⁡ ( 0 ) = g 0 f(0)=g_{0} is given by:

where:

f ( 0 ) ​ ( t ) f^{(0)}(t) is given by eq. ( 4.7 ), for t s ​ w = T 2 t_{sw}=\frac{T}{2} . The remaining f ( n ) ​ ( t ) f^{(n)}(t) can be obtained by induction. Suppose f ( n ) ​ ( t ) f^{(n)}(t) is given by eq. ( 4.12 ). The solution to the GDE in the interval [ ( n + 1 ) ​ T , ( n + 2 ) ​ T ) [(n+1)T,(n+2)T) is:

where C 1 , C 2 C_{1},C_{2} are integration constants. Let us impose the continuity of the function at t = ( n + 1 ) ​ T t=(n+1)T and t = ( n + 3 2 ) ​ T t=(n+\frac{3}{2})T to obtain the values of the integration constants:

This corresponds to eq. ( 4.12 ) for n → n + 1 n\to n+1 . Thus, by induction, expression ( 4.12 ) holds for any n n . ∎

The pdf given by ( 4.10 ) is still valid, with f 1 = g n ​ if ​ n ​ T ≤ t < ( ( n + 1 2 ) ​ T CLOSE f_{1}=g_{n}\ \textrm{if}\ {nT\leq t<((n+\frac{1}{2})T} and f 1 = ( E α ( − L ( s 2 ) ( n T + T 2 ) α ) ) − 1 × f_{1}=(E_{\alpha}(-L(s_{2})\left(nT+\frac{T}{2}\right)^{\alpha}))^{-1}\times × E α ​ ( − L ⁡ ( s 1 ) ​ ( n ​ T + T 2 ) α ) ​ g n ​ if ​ ( n + 1 2 ) ​ T ≤ t < ( n + 1 ) ​ T \times E_{\alpha}(-L(s_{1})\left(nT+\frac{T}{2}\right)^{\alpha})g_{n}\ \textrm{if}\ {(n+\frac{1}{2})T\leq t<(n+1)T} . This implies that the time scaling at time t t depends only on the parameter s s of the system at that time. Consequently, the phase diagram of fig. 3.1 is valid, adapting s s to the Mellin transform parameter that acts at the desired time.


## 5 Generalized diffusion on a linear chain

We consider here the diffusion of a particle along a linear chain or path graph P n P_{n} . The motivation of these simulations is provided by the diffusion of a protein along a DNA chain. We consider the double chains of DNA (see Fig. 5.1 a) as the path graph P n P_{n} . In doing so, we consider a pair of DNA bases, one from the 5’ chain and another from the 3’ chain, as a node of the path graph. The protein is then modeled as a particle diffusing on the linear chain. We consider here that the protein can diffuse by a combination of the following mechanisms: (i) one-dimensional diffusion or sliding, involving a random walk along the DNA without dissociation as illustrated in Fig. 5.1 b; (ii) jumping, where a protein moves over longer distances via dissociation and then rebinding at a distal location (see Fig. 5.1 c); (iii) intersegmental transfer, involving movement from one site to another via a looped intermediate (Fig. 5.1 d). The first process gives rise to normal diffusion, but we consider that at certain DNA regions the protein makes a longer exploration/repair which acts as a trap producing subdiffusive motion, which can be modeled by varying the exponent α \alpha of the Caputo fractional derivative. The mechanisms (ii) and (iii) clearly represent long-jumps controlled by the Mellin exponent in the transformed d d -path Laplacian. We should remark that other approaches have been reported in the literature to account for some aspects of the protein diffusion on DNA DNA_1 ; DNA_2 ; DNA_3 .

For the simulations we consider a path graph with N = 1001 N=1001 nodes. We always take as initial condition f n ​ ( 0 ) = δ n , 501 f_{n}(0)=\delta_{n,501} , i.e., we locate all the diffusive particle at the center of the linear chain. To obtain the probability density functions, we calculated eq. ( 3.3 ) using the algorithm from garrappa_computing_2018 for matrix Mittag-Leffler functions. We then fitted the time evolution of the maximum of the pdf and FWHM to a power law t γ t^{\gamma} , and compared the numerical exponent γ \gamma with the corresponding theoretical prediction. We have noticed that in the superdiffusive regime it is hard to precisely quantify the MSD, since the asymptotic behavior is reached for large times and erratic behaviors can appear in the transient regime (see Alves_characterization_2016 for a detailed discussion). Moreover, the FWHM method, while providing correct predictions, introduces a higher degree of inaccuracy in the exponent γ \gamma . Because of this, we use the method of the decay of the maximum to find the numerical exponent γ \gamma .

Our first target is to obtain a contour plot indicating how the exponent γ \gamma defining the type of diffusive regime changes with the values of the model parameters α \alpha and s s . The results are illustrated in Fig. 5.2 . We recall that for f max ​ ( t ) ∝ t − γ f_{\textnormal{max}}(t)\propto t^{-\gamma} :

i) γ < 0.5 \gamma<0.5 represents subdiffusion;

ii) γ = 0.5 \gamma=0.5 represents normal diffusion;

iii) γ > 0.5 \gamma>0.5 represents superdiffusion.

Therefore, we can see the curve with the value γ = 0.5 \gamma=0.5 in the Fig. 5.2 , which indicates the normal diffusion regime. When we move towards the right-upper corner of the plot, i.e., s → ∞ s\rightarrow\infty and α → 1 \alpha\rightarrow 1 , we are moving to a regime completely dominated by normal diffusion, which is represented by the standard graph diffusion equation. However, it is remarkable that even with strong long-jumps, e.g., s ≈ 2 , s\approx 2, we can still find regions of normal diffusion if the temporal memory parameter α \alpha is relatively small, e.g., α ≈ 0.6 \alpha\approx 0.6 . Over this curve we are in a superdiffusive regime and below it we are in the subdiffusive one. It is remarkable that there is an abrupt change of behavior at s = 3 s=3 , which matches the theoretical prediction that after this point the superdiffusive regime no longer exists. It can be seen that for s < 3 s<3 the contour lines of γ \gamma abruptly decay, while for s > 3 s>3 they are almost parallel to the x x -axis.

The main conclusion of this result is that, as proved analytically, the time and space GDE accounts for the three different diffusive regimes that can be observed in the diffusion of a protein on DNA: subdiffusion, normal diffusion and superdiffusion. In Fig. 5.3 we give an example of the time evolution of the diffusion of a particle along a linear chain of N = 1001 N=1001 nodes. We use α = 0.5 \alpha=0.5 , s = 2.5 s=2.5 , which according to the contour plot in Fig. 5.2 , corresponds to the subdiffusive regime. The value of γ \gamma calculated from the slope of the curve in Fig. 5.3 (b) is γ ≈ 0.33 ± 0.01 \gamma\approx 0.33\pm 0.01 and according to the one of Fig. 5.3 (c) is γ ≈ 0.31 ± 0.02 \gamma\approx 0.31\pm 0.02 . The analytical value is γ = 1 / 3 \gamma=1/3 .

We now turn our attention to the study of the time-varying GDE with periodic variation of the parameter s s . We consider that s s oscillates between the values s 1 = 200 s_{1}=200 , and s 2 = 2 s_{2}=2 . That is, for a given values of α \alpha the particle starts diffusing without long-jumps ( s 1 = 200 s_{1}=200 ). Then, after half a period of time it swaps to a regime where long-jumps are allowed ( s 2 = 2 s_{2}=2 ), and the process is repeated cyclically. We first fix α = 0.5 \alpha=0.5 and obtain the results illustrated in Fig. 5.4 (a). For 0 < t < 2 0<t<2 we have f max ​ ( t ) ≈ 0.3887 ​ t − 0.1987 f_{\textnormal{max}}(t)\approx 0.3887t^{-0.1987} and for 2 < t < 4 2<t<4 we obtain f max ​ ( t ) ≈ 0.4381 ​ t − 0.3982 . f_{\textnormal{max}}(t)\approx 0.4381t^{-0.3982}. That is, when α = 0.5 \alpha=0.5 the diffusive particle oscillates between two subdiffusive regimes. In fact, the global fit of the process is given by: f max ​ ( t ) ≈ 0.3671 ​ t − 0.2472 f_{\textnormal{max}}(t)\approx 0.3671t^{-0.2472} , which is a clear signature of subdiffusion.

We now consider the case where s 1 = 200 s_{1}=200 and s 2 = 2 s_{2}=2 as before, but using α = 0.9 \alpha=0.9 as illustrated in Fig. 5.4 (b). Here, f max ​ ( t ) ≈ 0.3368 ​ t − 0.3513 f_{\textnormal{max}}(t)\approx 0.3368t^{-0.3513} for 0 < t < 2 0<t<2 and f max ​ ( t ) ≈ 0.5108 ​ t − 1.133 f_{\textnormal{max}}(t)\approx 0.5108t^{-1.133} for 2 < t < 4 2<t<4 . The global process has scaling f max ​ ( t ) ≈ 0.2715 ​ t − 0.4651 f_{\textnormal{max}}(t)\approx 0.2715t^{-0.4651} . That is, the global process is a subdiffusive regime, although the diffusive particle alternates between a subdiffusive regime, i.e., γ ≈ − 0.3513 \gamma\approx-0.3513 for 0 < t < 2 0<t<2 , and a superdiffusive motion, γ ≈ − 1.133 \gamma\approx-1.133 for 2 < t < 4 2<t<4 .

The importance of this difference between the local temporal scale and the global one is revealed when we plot the decay of f max f_{\textnormal{max}} vs. t t for both values of the fractional parameter α \alpha as illustrated in Fig. 5.5 . As can be seen, the process where α = 0.5 \alpha=0.5 (blue circles) goes initially much faster than that where α = 0.9 \alpha=0.9 (red triangles). Then, there is a time in which the process with α = 0.9 \alpha=0.9 is much faster than that with α = 0.5 \alpha=0.5 . In other words, the combination of subdiffusion with superdiffusion, like when α = 0.9 \alpha=0.9 , allows the particle to make a slower initial exploration of a region of the linear chain in comparison with a subdiffusive-subdiffusive exploration. Additionally, the subdiffusive-superdiffusive process produces a faster global convergence of the process due to the long-jumps occurring in the superdiffusive regime. Notice that the subdifusive-subdifusive regime is obtained when the fractional parameter is relatively small, which correspond to systems with relatively large temporal memory. However, the subdiffusive-superdiffusive alternancy is obtained when the temporal memory is relatively small. Translating these results to the case of a protein diffusing along a DNA chain they mean that the alternant combination of sliding with jumping and/or intersegmental transfer offer some important advances to the exploration of the DNA by the protein. In this case, the slow subdiffusive regime allows a detailed exploration of small DNA regions to find potential targets and the fast superdiffusive regimes allow an exploration of vast regions of the DNA chain in relatively short times.


## 6 Conclusions and Outlook

We have defined a time and space GDE on undirected graphs/networks. It uses a combination of fractional derivatives and Mellin-transformed d d -path Laplacian operator. We have found analytically the solution of this equation and obtained the regions of the parametric space for which an infinite one-dimensional system displays, normal, sub- and superdiffusion. We have illustrated how this GDE can be applied to the study of the diffusion of proteins along the one-dimensional structure of DNA, where the mechanisms of sliding, hopping and intersegmental transfer, may give rise to normal, sub- and superdiffusive behaviors. We have also considered a GDE in which the parameters of the model change with time allowing the temporal alternancy of the normal and anomalous diffusive regimes.

The current model is useful for any discrete system in which any combination of the normal and anomalous diffusive regimes exists. The extension of this model to consider directed graphs, multigraphs and simplicial complexes can be performed to extend the areas of application of this approach. Also important should be the analysis of networks beyond the one-dimensional case presented here and to consider the influence of network topologies, e.g., small-worldness, scale-freeness, etc., on the diffusive dynamics. All in all we consider that this GDE will open new research avenues in the study of dynamical processes on graphs/networks.


## Acknowledgement

FD-D and EE acknowledge support from the Spanish Agency of Research (AEI) through Maria de Maeztu Program for units of Excellence in R&D (MDM-2017-0711). FD-D thanks finantial support MDM-2017-0711-20-2 funded by MCIN/AEI/10.13039/50110 0 011033 and by FSE invierte en tu futuro. EE thanks Grant PID2019-107603GB-I00 by MCIN/AEI /10.13039/50110 0 011033.


## References