## Autonomous Reshaping of Expression Landscapes by DNA Methylation

DNA methylation is usually treated as an epigenetic memory mark: transcriptional history is written into regulatory DNA and later stabilizes a chosen cell identity. This picture explains persistence, but it makes memory passive. Here we show that the same promoter-level coupling required for methylation memory can instead turn methylation into an internal control variable for regulatory dynamics. Transcription-factor occupancy protects regulatory DNA from methylation, while methylation shifts later transcription-factor binding thresholds. Under time-scale separation, this reciprocal loop separates into fast expression dynamics conditioned on methylation and a slow methylation flow written by expression. Minimal promoter, self-activation, and fate-toggle models show that this feedback does more than preserve a past state: it autonomously reshapes the expression landscape. In a methylation-coupled toggle, the preferred expression state can move continuously through single-well drift, allowing commitment without first entering a multiwell regime. Stochastic simulations further show that evolving methylation reduces fate reversals relative to a frozen landscape, making weak early expression bias more predictive of later fate. These results recast DNA methylation from a downstream stabilizer of cell identity into a slow dynamical coordinate that can help determine how regulatory states are chosen.


## Introduction

DNA methylation is commonly treated as an epigenetic memory mark: transcriptional history is recorded in methylation, which later stabilizes the resulting regulatory state and cell identity 5 ; 23 ; 2 ; 11 . This view reduces methylation-transcription coupling to a temporal sequence in which expression first chooses a state and methylation preserves it. The sequence explains why differentiated states persist, but it hides the dynamical premise on which memory depends. For methylation to record transcriptional history, expression must write it; for that memory to matter, methylation must be read by future expression.

Recent studies reveal a potential molecular mechanism for this write-read loop. Transcription factor occupancy and methylation machinery can compete at promoters and other regulatory DNA: bound transcription factors (TFs) can protect CpG-rich regions from de novo methylation or favor demethylation 6 ; 25 ; 30 ; 12 ; 10 ; 11 , while methylation can reduce later transcription factor binding or shift effective binding thresholds 34 ; 17 ; 35 ; 15 ; 10 ; 9 . This competition places writing and reading in the same local circuit, rather than in separate developmental stages.

Related theory has begun to treat epigenetic state as a dynamical partner of gene regulation. DNA-methylation models show that methylation can shift stability boundaries and basins of attraction 9 , while chromatin-state and slow-promoter models show that slow regulatory variables can reshape probability landscapes, generate hysteresis or homeorhesis, and stabilize memory 4 ; 29 ; 8 ; 26 ; 1 . Beyond shifting fate stability and basin structure, how does promoter-level methylation–transcription coupling change regulatory dynamics?

We answer this question with a sequence of minimal models. A single regulatory locus, motivated by recent promoter-memory experiments 11 , first isolates residual methylation as the slow coordinate left by promoter activity. Adding self-activation then reveals how this memory coordinate can become an internal control variable for the evolution of expression landscape. Finally, in a fate toggle, the same loop produces single-well drift: a commitment mode in which the preferred expression state moves continuously, rather than emerging through a classical bifurcation of a Waddington-like landscape 18 ; 16 ; 13 ; 28 . Together, these examples show that methylation not only preserves a chosen fate, but also affects fate decisions by reshaping regulatory dynamics.


## Results

We first strip the coupling down to a single regulatory locus. Consider a CpG-rich promoter exposed to a transcription factor or inducer with effective concentration x x (Fig. 1 a). Transcription factors and methylation enzymes compete at the regulatory sequence 9 ; 10 ; 14 ; 19 ; 22 . In this local circuit, TF occupancy protects the promoter from methylation, while methylation raises the threshold for later occupancy. The promoter state is therefore written by past occupancy and read by future occupancy.

The readout is transcription factor binding. Fast binding gives the occupancy

where n = 4 n=4 is the cooperativity constant, m ∈ [ 0 , 1 ] m\in[0,1] is the fraction of promoter CpGs that are methylated, and K ⁡ ( m ) K(m) is the methylation-dependent effective dissociation constant, equivalently the half-saturation concentration. Methylation changes TF occupancy by changing binding free energy 31 ; 36 ; 20 . Rather than model each CpG separately, we summarize the effect of methylation by a first-order expansion of the binding energy around the resting level m 0 m_{0} .

Here β = 1 / ( k B ​ T ) \beta=1/(k_{B}T) is the Boltzmann factor and ε 1 < 0 \varepsilon_{1}<0 , so that increasing methylation raises K ⁡ ( m ) K(m) and shifts the dose response to higher TF concentration.

The write arm is promoter methylation dynamics:

Here r m r_{m} and p m p_{m} are the demethylation and methylation rates, respectively. The factor ( 1 − h ) (1-h) implements promoter protection: methylation enzymes act most effectively when the promoter is unoccupied, and are excluded as TF occupancy increases. Together, the read and write arms close the minimal promoter loop.

This minimal loop gives a theoretical interpretation of recent promoter-memory experiments in mammalian cells, where two sequential stimuli were used to separate priming from the later response 11 . A first stimulus primes the locus, a stimulus-free interval removes the immediate occupancy response, and a second stimulus measures the shifted dose response (Fig. 1 b). Priming shifts the second dose response relative to the unprimed locus (Fig. 1 c), and the shift grows with the strength and duration of the first stimulus (Fig. 1 d). The collapse in Fig. 1 e identifies methylation as a sufficient memory variable: different intensity–duration histories produce the same shift in the second dose response whenever they leave the same residual methylation deviation Δ ​ m \Delta m . Residual methylation therefore compresses past regulatory activity into the variable that controls the next promoter response.

In the single-locus model, x x is imposed from outside. The next step is to let the variable that reads the promoter be produced by the circuit itself. The minimal closure is positive autoregulation: the gene product x x activates its own production through the same promoter response, whose threshold depends on methylation (Fig. 2 a). The expression dynamics are

with promoter methylation following the aforementioned dynamics, Eq. ( 3 ). Figure 2 b shows the flow field of this two-dimensional dynamical system. The arrows are nearly horizontal over most of the ( x , m ) (x,m) plane, consistent with rapid transcriptional response and slow methylation turnover 21 ; 7 . The nullclines show the complementary effect of methylation on the fast subsystem: at fixed m m , the circuit is an ordinary self-activating gene with a methylation-dependent activation threshold, and changing m m changes the number, position, and stability of the expression fixed points.

Such separation of time scales allows us to do a quasi-steady-state (adiabatic) approximation. For each fixed methylation level, the fast expression dynamics relax to a stable branch x ∗ ​ ( m ) x^{\ast}(m) (Fig. 2 c), where x ∗ ​ ( m ) x^{\ast}(m) is a stable root of the deterministic drift in Eq. ( 4 ), namely d ​ x / d ​ t | x = x ∗ ​ ( m ) = 0 \left.dx/dt\right|_{x=x^{\ast}(m)}=0 . Plugging h ​ ( x ∗ ​ ( m ) , m ) h(x^{\ast}(m),m) into Eq. ( 3 ) then gives the autonomous methylation dynamics m ⁡ ( t ) m(t) . Figure 2 d shows the direction and fixed points of this slow dynamics.

To represent these regulatory dynamics geometrically, we introduce an expression landscape. At fixed methylation, the remaining fast coordinate is one-dimensional, so the deterministic regulatory drift can be represented by an effective potential,

Stable expression states are minima of U ⁡ ( x , m ) U(x;m) . This deterministic potential is the small-noise limit of a landscape description; when intrinsic noise is large, the relevant object is instead the free-energy landscape U ⁡ ( x , m ) = − log ⁡ P ss ​ ( x | m ) U(x;m)=-\log P_{\mathrm{ss}}(x|m) , where P ss ​ ( x | m ) P_{\mathrm{ss}}(x|m) is the steady-state distribution of expression at fixed methylation 18 .

In a Waddington-style picture, landscape changes are usually driven by external developmental signals or imposed control parameters. Here, if methylation is ignored or held fixed, the self-activating gene has the usual static bistable landscape: in the absence of external input, the surface does not change over time (Fig. 2 e). With methylation feedback active, by contrast, the landscape U ⁡ ( x , m ) U(x;m) reshapes itself as the internal variable m m evolves. Different initial methylation states select different branches of this autonomous landscape motion; along each branch, one well becomes dominant and deepens over time (Fig. 2 f). Trajectories simulated from the full two-dimensional model, Eqs. ( 3 ) and ( 4 ), follow the moving landscape derived from the adiabatic approximation.

The same feedback becomes more consequential in a fate circuit. We embed it in a toggle switch, the minimal architecture for two mutually exclusive expression states 18 ; 1 . The two genes, x x and y y , self-activate, repress each other, and carry separate promoter methylation states ( m x , m y ) (m_{x},m_{y}) (Fig. 3 a). The fast expression dynamics are

Each promoter follows the methylation dynamics in Eq. ( 3 ); h ⁡ ( x , m x ) h(x,m_{x}) and h ⁡ ( y , m y ) h(y,m_{y}) govern both self-activation and methylation dynamics at the corresponding promoters, respectively.

We initialize the toggle near a symmetric, highly methylated state, m x ≃ m y ≃ m 0 = 0.8 m_{x}\simeq m_{y}\simeq m_{0}=0.8 , so that 80% of CpGs are methylated at both modeled promoters. This high-methylation starting point is consistent with genome-wide methylomes of human embryonic stem cells, where about 80% of CG observations are methylated 24 . As above, we use an adiabatic approximation to derive the autonomous dynamics of the slow variables, methylation ( m x , m y ) (m_{x},m_{y}) . For each fixed ( m x , m y ) (m_{x},m_{y}) , we find the stable roots ( x ∗ , y ∗ ) (x^{\ast},y^{\ast}) of the deterministic expression dynamics in Eqs. (6–7), then plug the corresponding occupancies h ⁡ ( x ∗ , m x ) h(x^{\ast},m_{x}) and h ⁡ ( y ∗ , m y ) h(y^{\ast},m_{y}) into the methylation dynamics. This gives an autonomous flow for ( m x , m y ) (m_{x},m_{y}) (Fig. 3 b). The ensemble of simulated methylation dynamics agrees well with the prediction from the adiabatic approximation (Fig. 3 c).

To connect this methylation flow to fate choice, we construct the expression landscape. In a toggle switch, the difference x − y x-y is the natural coordinate of fate asymmetry. We therefore project the deterministic drift in Eqs. (6–7) onto this direction and integrate the projected force to obtain an effective landscape along x − y x-y . There exist two branches of landscapes, selected by the initial methylation state and corresponding to the two differentiation directions. Strikingly, along each branch the landscape contains a single well whose minimum drifts toward one fate and deepens over time (Fig. 3 e).

Because the landscape is fully controlled by ( m x , m y ) (m_{x},m_{y}) , we can classify methylation space by the number of wells N wells N_{\rm wells} in the landscape. Figure 3 d marks regions with N wells = 1 , 2 , N_{\rm wells}=1,2, or 3 3 . Trajectories starting near ( m 0 , m 0 ) (m_{0},m_{0}) remain in the N wells = 1 N_{\rm wells}=1 region, showing that commitment need not proceed through the birth of two competing fate wells. We call this mode single-well drift: the preferred expression state moves continuously under autonomous methylation feedback, in contrast to the bifurcation picture in which fate choice is explained by the emergence of multistability in the landscape.

Single-well drift also changes what an early expression bias means. In a frozen landscape, a small value of x − y x-y before clear separation is likely a reversible fluctuation. Along an autonomously moving landscape, the same small asymmetry can already mark the branch the trajectory is following. This might provide a mechanism for lineage-tracing observations in which early transcriptional bias contains information about later fate before large expression differences are visible 33 .

We measure reversibility of transcriptional states by the flip ratio : the fraction of trajectories whose final fate has the opposite sign from their early expression bias (Methods). We compare evolving methylation from variable or identical initial conditions with frozen methylation (Fig. 4 a). The variance of x − y x-y serves as a common clock for visible fate separation. As this variance grows, the flip ratio decreases in all ensembles (Fig. 4 b). At the same variance, however, both settings with methylation dynamics have lower flip ratios than the frozen control. The same visible expression separation is therefore more predictive when the landscape can autonomously reshape.

At Var ⁡ ( x − y ) = 0.05 \mathrm{Var}(x-y)=0.05 , the two settings with methylation dynamics have similar flip ratios, and both are notably lower than the case with frozen methylation (Fig. 4 c). Initial methylation heterogeneity is therefore not the main source of the effect. The decisive ingredient is autonomous landscape evolution. A weak expression bias becomes encoded in the slow coordinate and reappears as a regulatory preference before large expression differences have appeared.


## Discussion

These results turn DNA methylation from a regulatory memory into a dynamical control variable. Once promoter methylation is allowed to evolve with regulatory activity, it no longer serves only as a record of the past. It parameterizes the fast expression landscape and changes the regulatory conditions encountered next. The landscape can therefore change without an external schedule.

This view extends, rather than replaces, landscape theory. Waddington-like landscapes have been quantified using attractors, stationary distributions, and quasi-potentials for gene-regulatory networks 18 ; 3 ; 32 ; 27 . Epigenetic feedback has also been proposed to generate homeorhetic landscape motion 26 , and slow promoter-state dynamics can generate multimodal expression landscapes, including in toggle switches 1 . Our contribution is to derive this motion from a local promoter closure rather than impose a time-dependent landscape. The same model specifies both the methylation-conditioned expression landscape and the slow dynamics that reshape it from within.

This landscape analysis reveals single-well drift as a new commitment mode. It allows cell fate decision without the observed trajectory entering a multiwell regime. Single-well drift should not be read as a replacement for bifurcation. Other parameter regimes of the same toggle contain multiple wells, and external signals can still drive conventional landscape branching. The specific point is that a slow internal coordinate can move the preferred expression state before the observed trajectory enters a multiwell regime. This changes how early fate bias can be interpreted. In a fixed landscape, weak expression asymmetry before visible separation is likely reversible. With feedback, the same asymmetry begins to alter future regulatory conditions. This might provide a mechanism for lineage-tracing observations in which early transcriptional bias predicts later fate before large expression differences are apparent 33 .

The construction is deliberately minimal. The methylation state is represented by a mean promoter coordinate, methylation-dependent binding is reduced to one energy parameter, and the landscapes used in the main text are deterministic small-noise effective potentials rather than full nonequilibrium quasi-potentials of the joint slow-fast stochastic system. These simplifications would not change the central lesson: a molecular memory mark can become an internal control variable for the future dynamics of gene regulation.


## References


## Methods


## Derivation of the methylation-dependent binding affinity

We model TF–DNA binding using a grand canonical statistical mechanical framework. A transcription factor occupies the regulatory DNA through n n simultaneous molecular contacts, where n n is the effective coordination number of the TF–DNA interaction. In the strongly cooperative (all-or-nothing) limit, only two binding states contribute appreciably to the partition function: the unbound state (reference energy zero) and the fully bound state in which all n n contacts are formed, each contributing a binding energy ε 0 > 0 \varepsilon_{0}>0 . Treating the TF-containing nucleus as a grand canonical reservoir with TF concentration x x (proportional to chemical activity e β ​ μ e^{\beta\mu} ), the partition function is

and the fractional saturation reads

which is a Hill function with half-saturation constant K n = e − n ​ β ​ ε 0 K^{n}=e^{-n\beta\varepsilon_{0}} . The Hill coefficient n n thus inherits its mechanistic interpretation from the coordination number of the binding event; in practice it is treated as an effective cooperativity parameter.

CpG methylation modifies binding through an additive free energy perturbation. Each of the n n contacts is destabilised when CpGs within the TF footprint are methylated: at fractional methylation level m m (measured relative to a resting reference m 0 m_{0} ), each contact contributes an extra energy ε 1 ​ ( m − m 0 ) \varepsilon_{1}(m-m_{0}) , with ε 1 < 0 \varepsilon_{1}<0 encoding the destabilising effect. Under the mean-field approximation that all contacts experience the same average methylation environment, the total binding free energy becomes

Substituting Δ ​ G ​ ( m ) \Delta G(m) into the grand canonical partition function gives the methylation-dependent saturation

with the half-saturation constant

Because ε 1 < 0 \varepsilon_{1}<0 , K ⁡ ( m ) K(m) increases monotonically with m m : higher methylation destabilises TF binding and shifts the dose–response curve to higher TF concentrations. Throughout this work we set ε 0 = 0 \varepsilon_{0}=0 , absorbing the reference-state affinity into the TF concentration scale, and fix n = 4 n=4 as the effective Hill coefficient.


## Model parameters

All three circuits share the same biophysical framework. Parameter values are summarised in Table 1 ; the resting methylation level in the absence of TF occupancy is m 0 = p m / ( p m + r m ) m_{0}=p_{m}/(p_{m}+r_{m}) .


## Methylation memory loop

Model equations and parameters. TF binding and dissociation equilibrate on timescales of seconds to minutes—far faster than methylation turnover (hours to cell divisions)—justifying a quasi-steady-state approximation for TF occupancy:

Methylation dynamics are governed by

where r m r_{m} and p m p_{m} are the basal demethylation and methylation rates, and c ≥ 0 c\geq 0 parametrizes enhanced demethylation when the locus is bound (TET recruitment upon TF occupancy). All simulations use c = 0 c=0 , reducing to

The resting methylation level is m 0 = p m / ( p m + r m ) m_{0}=p_{m}/(p_{m}+r_{m}) . Equations are integrated numerically using the forward Euler method with time step Δ ​ t = 0.1 \Delta t=0.1 . Parameter values are listed in Table 1 .

Two-stimulus protocol. The inducer concentration x ⁡ ( t ) x(t) follows a piecewise-constant waveform: a first stimulus of strength x 1 = 2 x_{1}=2 is applied during [ 0 , T 1 ] [0,\,T_{1}] with T 1 = 10 T_{1}=10 ; after a stimulus-free interval Δ ​ T = 2 \Delta T=2 , a second stimulus of variable strength x 2 x_{2} is applied during [ T 1 + Δ ​ T , T 1 + Δ ​ T + T 2 ] [T_{1}+\Delta T,\;T_{1}+\Delta T+T_{2}] with T 2 = 2 T_{2}=2 . For the naive (unprimed) condition, the first stimulus is omitted and the system is initialised at m 0 m_{0} .

EC50 definition. For each second-stimulus strength x 2 x_{2} drawn from 100 evenly spaced values in [ 0 , 2 ] [0,2] , the response is the time-averaged TF occupancy h ⁡ ( x , m ) h(x,m) during the final time unit of the second stimulus. The EC50 is the x 2 x_{2} value at which the response equals half its population maximum, determined by linear interpolation between adjacent data points. Memory strength is reported as the EC50 shift:

which is positive when priming increases sensitivity (lowers the effective EC50).


## Self-tilting expression landscape

Model equations and parameters. Gene expression and methylation evolve as coupled Itô stochastic differential equations:

where d ​ W x dW_{x} and d ​ W m dW_{m} are independent Wiener increments. These are integrated via the Euler–Maruyama scheme ( Δ ​ t = 0.01 \Delta t=0.01 ), with x x clipped below zero and m m clipped to [ 0 , 1 ] [0,1] after each step. Parameter values are listed in Table 1 .

Effective potential. For a fixed methylation level m m , the effective potential is obtained by numerical integration of the deterministic drift:

evaluated on a uniform discrete grid in x x . This frozen- m m construction is used to interpret Fig. 2 e. Fig. 2 b shows the deterministic skeleton (vector field, nullclines, and fixed points) in the ( x , m ) (x,m) plane. The dynamic landscape panel Fig. 2 f is obtained by evaluating U ⁡ ( x , m ⁡ ( t ) ) U(x;\,m(t)) at successive snapshots along a representative methylation trajectory m ⁡ ( t ) m(t) .

Quasistatic reduction (Figs. 2 c–d). For each m m on a dense grid, attractors of the fast equation (roots of the x x -drift) are found numerically. A single attracting branch x ∗ ​ ( m ) x^{\ast}(m) is followed by continuity in m m so that x ∗ x^{\ast} selects the same expression state across adjacent m m where multiple stable roots exist. The reduced drift is F ⁡ ( m ) = − r m ​ m + p m ​ ( 1 − m ) ​ ( 1 − h ⁡ ( x ∗ ​ ( m ) , m ) ) F(m)=-r_{m}m+p_{m}(1-m)\bigl(1-h(x^{\ast}(m),m)\bigr) , using the same h ⁡ ( x , m ) h(x,m) as in the full model. Fig. 2 d plots F ⁡ ( m ) F(m) (effective slow flow) and marks its zeros; the one-dimensional potential − ∫ F ( m ) d m -\int F(m)\,dm is evaluated by trapezoidal quadrature for display where needed.


## Methylation-coupled fate toggle

Model equations and parameters. We model the fate decision process as symmetry breaking from a symmetric initial condition toward one of two stable differentiated attractors 28 ; 16 ; 13 , consistent with the established view that bipotent progenitor cells reside near a saddle point separating two fate basins. The methylation-coupled toggle switch evolves as:

with h ⁡ ( x , m ) = x n / ( x n + K n ​ ( m ) ) h(x,m)=x^{n}/\bigl(x^{n}+K^{n}(m)\bigr) as in the single-gene circuits above. Parameter values are listed in Table 1 .

Reduced dynamics and landscapes (Fig. 3 b–e). Lineage commitment is captured by the expression asymmetry v = ( x − y ) / 2 v=(x-y)/2 , which changes sign at fate reversal, while the total expression u = ( x + y ) / 2 u=(x+y)/2 sets the overall activity level. Fig. 3 b sketches the quasistatic reduction of the four-dimensional stochastic dynamics to slow methylation coordinates ( m x , m y ) (m_{x},m_{y}) . Fig. 3 c compares ensemble-mean methylation trajectories from the full model (dashed) with trajectories of the reduced dynamics (solid). Fig. 3 d shows the reduced vector field in ( m x , m y ) (m_{x},m_{y}) together with a map of the number of stable attractors of the frozen fast ( x , y ) (x,y) subsystem (white: one attractor; lighter and darker shading: two and three attractors, respectively); overlaid trajectories illustrate differentiation within the single-attractor region. Fig. 3 e displays the effective expression-space potential U ⁡ ( x , y ) U(x,y) at successive methylation states along a representative trajectory.

For given ( m x , m y , u ) (m_{x},m_{y},u) , the drift along v v is

where F ⁡ ( x , y , m ) = x n / ( x n + K n ​ ( m ) ) + k n / ( y n + k n ) − γ ​ x F(x,y,m)=x^{n}/(x^{n}+K^{n}(m))+k^{n}/(y^{n}+k^{n})-\gamma x is the deterministic drift of x x . The corresponding effective potential along v v is

evaluated by the trapezoidal rule on a uniform grid in v v and normalised so that U ⁡ ( 0 ) = 0 U(0)=0 . The dynamic landscape in Fig. 3 e is generated along a trajectory by evaluating the expression-space effective potential U ⁡ ( x , y ) U(x,y) described in the figure caption at successive ( m x ​ ( t ) , m y ​ ( t ) ) (m_{x}(t),m_{y}(t)) , using the deterministic drift F F at frozen methylation.

Flip ratio (Fig. 4 ). We simulate N = 500 N=500 independent trajectories for each of three conditions:

Evolving landscape + m 0 m_{0} variance (Group A): methylation dynamics fully active; m x , 0 m_{x,0} and m y , 0 m_{y,0} drawn independently from 𝒩 ⁡ ( m 0 , σ m 0 2 ) \mathcal{N}(m_{0},\,\sigma_{m_{0}}^{2}) with σ m 0 = 0.05 \sigma_{m_{0}}=0.05 .

Evolving landscape (Group B): methylation dynamics active; m x , 0 = m y , 0 = m 0 = 0.8 m_{x,0}=m_{y,0}=m_{0}=0.8 .

Frozen landscape (Group C): methylation dynamics inactive ( r m = p m = σ m = 0 r_{m}=p_{m}=\sigma_{m}=0 ); m x m_{x} and m y m_{y} are held fixed at m 0 = 0.8 m_{0}=0.8 . To ensure a fair comparison, the baseline binding energy ε 0 \varepsilon_{0} is adjusted from 0 0 to − ln ⁡ ( 0.525 ) ≈ 0.64 -\ln(0.525)\approx 0.64 , so that the steady-state attractor positions of the frozen-landscape system match those of the Evolving landscape condition. This is equivalent to fixing methylation at an effective level m eff ≈ 0.16 m_{\rm eff}\approx 0.16 , mimicking the committed low-methylation state of the high-expression gene in the autonomously evolving model. Differences in flip ratio between conditions therefore reflect the autonomous landscape evolution itself, rather than differences in attractor location.

All trajectories are initialised at x 0 = y 0 = 1 / γ x_{0}=y_{0}=1/\gamma . At each time step T T , the population variance Var ⁡ ( x ⁡ ( T ) − y ⁡ ( T ) ) \mathrm{Var}(x(T)-y(T)) is recorded, and the instantaneous asymmetry sign sign ⁡ ( x ⁡ ( T ) − y ⁡ ( T ) ) \mathrm{sign}(x(T)-y(T)) of each trajectory is taken as its early fate bias at T T . After the simulation reaches steady state, each trajectory is assigned a final fate based on sign ⁡ ( x final − y final ) \mathrm{sign}(x_{\rm final}-y_{\rm final}) . The flip ratio at time T T is the fraction of trajectories whose early fate bias at T T disagrees with their final fate, averaged across the two sub-populations ( x ⁡ ( T ) > y ⁡ ( T ) x(T)>y(T) and x ⁡ ( T ) < y ⁡ ( T ) x(T)<y(T) ). For Fig. 4 b, the flip ratio is plotted as a continuous function of Var ⁡ ( x ⁡ ( T ) − y ⁡ ( T ) ) \mathrm{Var}(x(T)-y(T)) . For Fig. 4 c, the flip ratio is extracted at the time T T when the population variance first reaches Var ⁡ ( x − y ) = 0.05 \mathrm{Var}(x-y)=0.05 .


## Code availability

Code availability statement to be added.