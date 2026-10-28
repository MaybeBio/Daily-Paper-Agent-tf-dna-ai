Segmentation and genome annotation algorithms

Maxwell W. Libbrecht ( 0000-0003-2502-0262 ) 1☯* , Rachel C.W. Chan ( 0000-0003-1009-6379 ) 2,3☯ , Michael M. Hoffman ( 0000-0002-4517-1562 ) 2,3,4,5*

1 School of Computing Science, Simon Fraser University, Burnaby, BC, Canada

2 Department of Computer Science, University of Toronto, Toronto, ON, Canada

3 Princess Margaret Cancer Centre, Toronto, ON, Canada

4 Department of Medical Biophysics, University of Toronto, Toronto, ON, Canada

5 Vector Institute for Artificial Intelligence, Toronto, ON, Canada

☯These authors contributed equally to this work.

* maxwell_libbrecht@sfu.ca, michael.hoffman@utoronto.ca


## Abstract

SAGA ( SAGA ) algorithms are widely used to understand genome activity and gene regulation. These algorithms take as input epigenomic datasets, such as ChIP-seq ( ChIP-seq ) measurements of histone modifications or transcription factor binding. They partition the genome and assign a label to each segment such that positions with the same label exhibit similar patterns of input data. SAGA algorithms discover categories of activity such as promoters, enhancers, or parts of genes without prior knowledge of known genomic elements. In this sense, they generally act in an unsupervised fashion like clustering algorithms, but with the additional simultaneous function of segmenting the genome. Here, we review the common methodological framework that underlies these methods, review variants of and improvements upon this basic framework, catalogue existing large-scale reference annotations, and discuss the outlook for future work.


## Background and motivation

High-throughput sequencing technology has enabled numerous techniques for genome-scale measurement of chemical and physical properties of chromatin and associated molecules in individual cell types. Using sequencing assays, the ENCODE ( ENCODE ) Project, the Roadmap Epigenomics Project, and myriad individual researchers have generated thousands of such datasets. These datasets quantify various facets of gene regulation such as genome-wide transcription-factor binding, histone modifications, open chromatin, and RNA transcription. Each dataset measures a particular activity at billions of positions, and the collection of datasets does so in hundreds of samples across a variety of species and tissues. Transforming these quantifications of diverse properties into a holistic understanding of each part of the genome requires effective means for summarization. SAGA algorithms ( 1 ) have emerged as the predominant way to summarize activity at each position of the genome, distilling complex data into an interpretable précis of genomic activity.

SAGA algorithms take as input a collection of genomic datasets, such as ChIP-seq measurements of histone modifications or of transcription factor binding ( Figure 1 ). The SAGA task is to use the input datasets to partition the genome into segments and assign a label to each segment. SAGA algorithms perform this task in a way that leads to positions with the same label having similar patterns in the input data.

The first SAGA methods were developed in the 2000s, but have increased in usage recently, thanks to the wide availability of genomic datasets ( Table 1 ). Large-scale genomic profiling projects such as ENCODE [ 29 ] and Roadmap Epigenomics [ 7 ] produced SAGA annotations as a primary output. Researchers have developed a large variety of SAGA strategies with the goal of improving upon the basic SAGA framework.

In this review, we summarize the main strategies used by most SAGA methods. Then, we discuss differences between methods, the challenges they face, and the outlook for future work.


## Input data


## Experimental assays used for input data

SAGA methods typically use as input a number of different experimental datasets, each describing some local property of the genome [ 30 ] . Such properties might include chromatin accessibility or presence of some DNA-binding protein. Although input data initially came from microarray methods such as tiling arrays [ 31 ] , they now usually come from sequence census assays [ 32 ] .

A standard collection of input datasets might measure histone modifications or DNA-binding proteins (using assays like ChIP-seq [ 33 ] or CUTnRUN ( CUTnRUN ) [ 34 ] ), and chromatin accessibility (using assays like DNase-seq ( DNase-seq ) [ 35 , 36 ] or ATAC-seq [ 37 ] ). Supplying \@iaci SAGA SAGA algorithm with datasets that measure chromatin activity yields an output annotation that captures the regulatory state of chromatin. Creating these chromatin activity annotations has served as the predominant use of SAGA methods thus far.

Less frequently, researchers have gone beyond measurements of chromatin and DNA-binding proteins and have used SAGA methods for other kinds of data. The output annotation summarizes the input datasets, so the choice of input greatly influences the annotation’s content and its subsequent interpretation. SAGA methods can work for any sort of dense linear signal along the genome. Individual studies have applied it DNA replication timing data [ 3 , 24 , 27 ] , interspecies comparative genomics data [ 25 ] , and RNA-seq data [ 28 ] . Other studies have even found ways to incorporate non-linear chromatin 3D genome organization data into the SAGA framework [ 3 , 27 ] .


## Signal representation of genomic assays

Most genomic assay data so far has come from bulk samples of cells. These data depict a noisy mixture of sampling an assayed property from the many cells within the population. These cells may represent subpopulations of slightly different types, or within different cell cycle stages. Thus, each subpopulation might have different characteristics in the assayed properties. In the mixture of cell subpopulations, only frequently sampled properties will rise above background noise. By comparison, less frequently sampled properties seen in a minority of cells, may remain indistinguishable from background noise.

Often, the property examined by an epigenomic assay is exhibited or not exhibited by some position of a single chromosome in a single cell, with no gradations between the extremes. For example, at some nucleotide of one chromosome in a single cell, an interrogated histone modification is either present or it is not. A single diploid cell has two copies of the chromosome. Thus, at that position, each eudiploid cell can have only 0, 1, or 2 instances of the histone modification.

Summing or averaging discrete counts over a population of cells leads to a representation of the assay data called “signal”. Signal appears as a continuous-scale measurement. Signal arises, however, only from the aggregation of position-specific properties, which in each cell may have only a small number of potential ordinal value at the moment of observation.

Unlike epigenomic assays, transcriptomic assays can measure any number of transcript copies of one position per cell. Despite similar data representations, one must avoid the temptation to interpret epigenomic signal intensity as one might interpret transcriptomic signal intensity. For a transcriptomic assay, greater signal intensity for a transcriptomic assay might reflect a greater “level” of some transcriptional property within each cell. For an epigenomic assay, greater signal intensity indicates primarily that a higher number of cells within a sample have the property of interest.

In both the epigenomic and transcriptomic cases, it remains difficult or impossible to untangle the contribution to higher signal intensity that arises from frequency of molecular activity within each cell of a subpopulation from that from the composition of subpopulations within a whole bulk population. Improvements in single-cell assays, however, may enable SAGA algorithms on data from single cells in the near future (see “Outlook for future work”).


## Preprocessing of input data

SAGA methods generally use a signal representation of the input data. This signal representation originates from raw experimental data, such as sequencing reads, by way of a preprocessing procedure. For simplicity, we describe the steps of preprocessing as if a human analyst conducted them all individually, although some SAGA software packages might perform some steps without manual intervention:

Required preprocessing for all SAGA methods:

The analyst transforms the experimental data into raw numeric signal data.

For sequencing data, the analyst:

Aligns each sequencing read to the reference genome,

May choose to extend each read to an estimated length of the DNA fragment it begins, and

Computes the number of reads per base or extended reads per base for each genomic position [ 9 , 10 ] .

For microarray data, the analyst:

Acquires microarray signal intensity for the experimental sample and for a control sample, and

Computes the ratio of experimental intensity to control intensity.

The analyst chooses units to represent the strength of activity at each position and may perform further transformation of the raw numeric signal data into these units.

For sequencing data, the analyst commonly uses one of:

Read count (no transformation),

Fold enrichment of observed data relative to a control [ 6 ] , or

− log 10 -\log_{10} Poisson p-values indicating the likelihood of statistically significant peaks relative to control [ 19 ] .

The latter two units can mitigate experimental artifacts because they compare to a control experiment such as a ChIP input control.

For microarray data, the analyst commonly performs log 2 \log_{2} transformation of the intensity ratios [ 38 , 4 , 39 ] .

Optional preprocessing or preprocessing required only for specific SAGA methods:

The analyst may normalize data to harmonize signal across cell types [ 40 ] . Normalization proves especially important when annotating multiple cell types (see “Annotating multiple cell types”).

To prevent large outlier signal values from dominating the results, the analyst may transform signals using one of three variance-stabilizing transformations of each signal value x x :

asinh ⁡ x \asinh x [ 9 ] ,

log 2 ⁡ ( x + pseudocount ) \log_{2}(x+\text{pseudocount}) [ 19 ] , or

an empirical variance-stabilizing transformation [ 41 ] .

The analyst may downsample 1- bp \mathrm{bp} resolution signal into bins (see “Spatial resolution”). This involves computing one of:

Average read count,

Reads per million mapped reads fold enrichment [ 42 ] ,

Total count of reads [ 16 , 43 , 44 ] , or

Maximum count of reads of each bin [ 6 , 18 ] .

Binning greatly decreases the computational cost of the SAGA algorithm and can improve the data’s statistical properties.

The analyst may binarize numeric signal data into presence/absence values [ 2 , 45 , 12 , 21 , 46 ] . Binarizing signal simplifies analysis by avoiding issues related to the choice of units, but eliminates all but 1 bit 1\text{\,}\mathrm{bit} of information about signal intensity per bin.


## Missing data

Genomic assays almost always cannot produce signal for every region of the whole genome. Regions where an assay cannot provide reliable information about the interrogated property constitute “missing data” for that assay. Missing data in sequencing assays may arise due to unmappable sequences, which occur when repetitive reads do not uniquely map to a region [ 47 , 48 ] . Missing data in microarray assays comes from regions covered by no microarray probes. There are three main ways to treat regions of missing data: (1) by treating missing data as 0-valued data, (2) by decreasing the model resolution, averaging over available data so that the missing data has limited impact, or (3) statistical marginalization over the missing data [ 49 , 9 ] .

When analyzing coordinated assays across multiple cell types, researchers may have to contend with having no data on some properties within a subset of cell types. This represents another kind of missing data: one with an entire dataset missing rather than only data at specific positions. Researchers can impute [ 21 ] entire missing datasets through tools such as ChromImpute [ 50 ] , PREDICTD [ 51 ] or Avocado [ 52 ] . Alternatively they can use \@iaci SAGA SAGA model with built-in capability for handling the missing datasets [ 12 ] .


## HMM ( HMM ) formulation

Many SAGA methods rely on \@iaci HMM HMM , a probabilistic model of the relationships between sequences of observed events and the unobservable hidden states which generate the observed events. The structure of HMM , and similar models such as DBN [ 53 ] , naturally reflect the SAGA task of clustering observed data generated by processes that act on sequences of genomic positions.


## Simple HMM example

As an illustration of a simple HMM , consider a dog, Rover, and his owner, Thomas. Thomas is 5 years old and too short to see out of the windows in his home. Rover can leave the house through his dog door and loves taking walks, playing indoors, and napping. Every morning, he will either wait by the door for Thomas, play with his squeaky toys, or sleep in. Whichever action he takes depends on the weather he sees outdoors. For example, on rainy days Rover will more likely nap or play with his toys indoors.

Thomas must infer the state of the weather outside, hidden to him, based on the behavior he observes from Rover. Thomas knows the general weather patterns outside near his home—for example, that rainy weather likely continues across multiple days.

This scenario fits well into the \@iaci HMM HMM framework. It has a sequence of observations (Rover’s behavior) generated by hidden, non-independent unobservables (the weather outside). One would like to infer the sequence of hidden unobservables based on the sequence of observations.


## Mathematical formulation

A

B

Formally, we can define \@iaci HMM HMM over time t ∈ { 1 , … , T } t\in\{1,\dots,T\} as follows [ 54 , 55 ] . Let the sequence of observed events 𝑿 = { X t } t = 1 T \boldsymbol{X}={\{X_{t}\}}_{t=1}^{T} consist of each observed event X t X_{t} at every time t t . Let the sequence of hidden states 𝑸 = { Q t } t = 1 T \boldsymbol{Q}={\{Q_{t}\}}_{t=1}^{T} consist of each hidden state Q t Q_{t} at every time t t . Each Q t Q_{t} takes on a value q t q_{t} from a set of m m possible hidden state values ( Figure 2 a).

Under the Markov assumption, the probability of realizing state value q t + 1 q_{t+1} at the next time step t + 1 t+1 depends only on the current state value q t q_{t} :

We define the transition probability A ⁡ ( q t + 1 | q t ) = P ⁡ ( Q t + 1 = q t + 1 | Q t = q t ) A(q_{t+1}|q_{t})=P(Q_{t+1}=q_{t+1}|Q_{t}=q_{t}) , which reflects the frequency of moving from state q t q_{t} to state q t + 1 q_{t+1} .

We define the emission probability B ⁡ ( x t | q t ) = P ⁡ ( X t = x t | Q t = q t ) B(x_{t}|q_{t})=P(X_{t}=x_{t}|Q_{t}=q_{t}) as the probability that the observable X t X_{t} is x t x_{t} if the present hidden state Q t = q t Q_{t}=q_{t} . Specifically, we assume that B ⁡ ( x t | q t ) B(x_{t}|q_{t}) depends only on Q t = q t Q_{t}=q_{t} , such that

Finally, we define the hidden state probability at the first time step as π 0 ​ ( q 0 ) = P ⁡ ( Q 0 = q 0 ) \pi_{0}(q_{0})=P(Q_{0}=q_{0}) . We can fully define \@iaci HMM HMM M = ( A , B , π 0 ) M=(A,B,\pi_{0}) by specifying all of A A , B B and π 0 \pi_{0} .

In the case of Rover and Thomas, we have m = 2 m=2 possible hidden states (rainy, not-rainy) and 3 3 possible observations (Rover is napping, playing indoors, or waiting by the door). To Thomas, the hidden variable Q t Q_{t} captures the weather outside, while the observed variable X X captures Rover’s behavior. The probability of the state of the weather outside changing on a day-to-day basis is defined by the transition probabilities A A ( Figure 2 b). The probability of Rover’s behavior, given the weather, is defined by the emission probabilities B B .


## Algorithms for inference, decoding, and training

The main task one uses HMM for is to quantify how well some predicted sequence of hidden states fits the observed data. Other common tasks like decoding or training serve as variations of, or build on, this inference task.

In HMM inference, we can compute the likelihood of any sequence of hidden states 𝑸 \boldsymbol{Q} . We use the sequence of observed events 𝑿 \boldsymbol{X} and the model probabilities M M to compute the likelihood function P ⁡ ( 𝑿 | 𝑸 , M ) P(\boldsymbol{X}|\boldsymbol{Q},M) . The likelihood function is the probability that our predicted sequence of hidden states produced our observed sequence of observed states. We often compute the likelihood function using the forward-backward algorithm [ 56 , 57 ] .

Given a sequence of observed events 𝑿 \boldsymbol{X} , we often wish to know the maximum likelihood sequence of corresponding hidden states 𝑸 \boldsymbol{Q} . For example, if Thomas observes that in the past 3 mornings, Rover slept, played, and then slept again, what weather sequence outside is most likely?

To answer this question, we decode the optimal sequence of hidden states 𝒒 ∗ \boldsymbol{q}^{*} such that 𝒒 ∗ = arg ​ max 𝐐 ⁡ P ​ ( 𝐐 | 𝐗 , M ) \boldsymbol{q}^{*}=\argmax_{\boldsymbol{Q}}P(\boldsymbol{Q}|\boldsymbol{X},M) . The Viterbi algorithm [ 58 ] provides an efficient solution for this problem, making it unnecessary to compare the likelihood for every possible sequence of hidden states.

Usually, we do not know the model parameters ( A , B , π 0 ) (A,B,\pi_{0}) and must learn them from data. We define training as the process of learning these parameters, and training data as the sequence of observations upon which we learn. An efficient algorithm that finds the global optimum parameter values for some training data does not exist. Instead, researchers commonly train HMM using EM ( EM ) [ 59 ] algorithms such as the Baum-Welch algorithm [ 60 ] , which find a local optimum. Other reviews [ 54 ] describe inference and training methods in more detail.


## HMM for SAGA

We can readily apply the HMM formalization to genomic data for use in SAGA methods. Instead of time, we define the dynamic axis t t in terms of physical position along a chromosome. Each position t t refers to a single base pair or, in the case of lower-resolution models, a fixed-size region (see “Spatial resolution”). The observation at each genomic position usually represents genomic signal (see “Input data”). Each position’s hidden state represents its label (see “Understanding labels”). As a result, decoding the most probable sequence of hidden states reveals the most probable sequence of labels across the genome. We call this resulting sequence of labels an annotation.

Many SAGA methods use \@iaci HMM HMM structure [ 39 , 2 , 9 , 12 , 42 , 21 , 16 , 24 ] , or generalizations thereof. For example, DBN are generalizations of HMM that can model connections between variables over adjacent time steps. Methods such as Segway [ 9 ] use \@iaci DBN DBN model in their approach to the SAGA problem. This can make it easier to extend the model to tasks such as semi-supervised, instead of unsupervised, annotation [ 61 ] .


## Understanding labels

SAGA methods are unsupervised. The labels they produce usually begin with integer designations without any essential meaning. Ideally each label corresponds to a particular category of genomic element. To make this correspondence explicit, we must assign a biological interpretation, such as “Enhancer” or “Transcribed gene”, to each label.

Usually, one makes assignments of labels to biological interpretations in a post-processing step. In post-processing, a researcher compares each label to known biological phenomena and assigns an interpretation that matches the researcher’s understanding of molecular biology. For example, a label characterized by the histone modification H3K36me3 (associated with transcription) and enriched in annotated gene bodies might have the interpretation “Transcribed”. A label characterized by H3K27ac and H3K4me1, both histone modifications canonically associated with active enhancers, might have the interpretation “Enhancer” [ 29 ] .

The interpretation process provides an opportunity to discover new categories of genomic elements. For example, one SAGA study found that their model consistently produces a label corresponding to transcription termination sites. Previously, none had described a distinctive epigenetic signature for transcription termination [ 6 ] .

Manual interpretation proves time-consuming for human analysis. Applying SAGA to multiple cell types independently exacerbates this problem (see “Annotating multiple cell types”).

Two existing methods automate the label interpretation process: expert rules and machine learning. In both cases, an interpretation program considers the information that a researcher would use for interpretation. This includes examining the relationship between labels and individual input data properties. It also includes reviewing colocalization of labels with features in previously created annotations. These annotations may have come from SAGA approaches or other manual or automated methods.

In the expert rule approach, an analyst designs rules about what properties a given label must have to receive a particular interpretation. The analyst then applies these rules to assign interpretations to labels from all models [ 15 ] .

In the machine learning approach, one trains a classifier on previous manual annotations. The classifier then learns a model that assigns interpretations to labels given their properties [ 11 ] . One analysis [ 11 ] found that automatic interpretation agreed with manual for 77% of labels, compared to 19% expected by chance.


## Spatial resolution

Baroque music often employs a musical architecture known as “ternary form”. Specifically, pieces of this structure follow a general “ABA” pattern, whereupon the second “A” section recapitulates the first with some variation. Each section contains multiple musical “sentences”, which may repeat or vary. Just like linguistic sentences, each musical sentence contains clusters of notes, or motifs, between “breaths” in the musical articulation. Finer examination of the motifs shows they contain a few notes and chords each. Finer examination of the notes themselves shows they behave just like isolated phonemes in speech, with little meaning on their own.

The genome resembles a musical composition in that one observes different behaviors at different scales. The scale of genomic behavior one wishes to observe influences the choice of SAGA method and parameters chosen for the method. To observe nucleosome-scale behavior such as genes, promoters and enhancers, one desires ∼ 1 × 10 3 bp \sim 1\text{\times}{10}^{3}\text{\,}\mathrm{bp} segments. To describe behavior on the scale of topological domains [ 62 ] , one desires segments of length 1 × 10 5 bp to 1 × 10 6 bp 1\text{\times}{10}^{5}\text{\,}\mathrm{bp}1\text{\times}{10}^{6}\text{\,}\mathrm{bp} [ 17 , 3 , 1 ] .

The most important parameter influencing segment length is the underlying resolution of the SAGA method. As noted above (see “Input data”), most SAGA methods downsample data into bins. To observe nucleosome-scale segment lengths ( ∼ 1 × 10 3 bp \sim 1\text{\times}{10}^{3}\text{\,}\mathrm{bp} ), one should use one should use 100 bp to 200 bp 100\text{\,}\mathrm{bp}200\text{\,}\mathrm{bp} resolution [ 2 , 9 , 18 ] . To observe domain-scale segment lengths ( ∼ 1 × 10 5 bp \sim 1\text{\times}{10}^{5}\text{\,}\mathrm{bp} ), one should use ∼ 1 × 10 4 bp \sim 1\text{\times}{10}^{4}\text{\,}\mathrm{bp} resolution [ 4 , 3 , 27 ] . Segway [ 9 ] and RoboCOP [ 63 ] provide some of few SAGA methods optimized for single-base resolution inference, and can identify behavior on a 1 bp 1\text{\,}\mathrm{bp} scale. While most existing SAGA methods handle data at just one genomic scale, there exist methods capable of learning from data at multiple genomic scales [ 21 ] .

Limitations of of the experimental data itself influence the choice of SAGA model resolution. Spatial imprecision in ChIP-seq data gives it an inherent resolution of about 10 bp 10\text{\,}\mathrm{bp} . More precise assays such as ChIP-exo [ 64 ] and ChIP-nexus [ 65 ] can approach 1 bp 1\text{\,}\mathrm{bp} resolution. Conversely, assays like DamID ( DamID ) and Repli-seq have a coarser resolution of ≥ 100 bp \geq 100\text{\,}\mathrm{bp} .

The desired scale may also influence the choice of input data. When aiming to annotate at the domain scale, one should include data with activity at this scale, such as replication time data and Hi-C data [ 4 , 3 , 27 , 24 ] . The inclusion of long-range contact information from Hi-C data poses a challenge because standard algorithms for HMM cannot be used for a probabilistic model that includes long-range dependencies. Therefore, one must instead use alternative approaches such as graph-based regularization [ 3 ] or approximate inference [ 27 ] .

SAGA methods model segment length through their transition parameters. HMM models assume a geometric distribution in determination of a segment’s length [ 66 ] . Related DBN methods can include constraints to tune segment length further. Constraints include the enforcement of a minimum or maximum segment length [ 9 ] . Enforcement of a minimum segment length ensures that one does not obtain segments shorter than the effective resolution of the underlying data or biological phenomena. Probabilistic models often additionally use a prior distribution on the transition parameters during training to encourage them to produce shorter or longer segment lengths.


## Choosing the number of labels

Most SAGA methods require the user to define the number of labels. Using more labels increases the granularity of the resulting annotation at the cost of added complexity. Typically, the number of labels ranges from 5–20, with more recent work favoring 10–15 labels.

One might think to make the choice of number of labels automatically with a statistical approach. The AIC ( AIC ), BIC ( BIC ), and FIC ( FIC ) [ 67 ] measure the statistical support a particular number of labels has. Instead of a fixed number of labels, one may give the model flexibility to choose the number of labels during training and include a hyperparameter that encourages it to choose a higher or lower number [ 14 ] . Or one might define labels according to local minima in an optimization based on a network model of assays [ 46 ] . One could even exhaustively assign a separate label to every observed presence/absence pattern in binary data [ 43 ] .

In practice, however, researchers rarely use these statistical approaches for determining the number of labels. Optimizing an information criterion does not necessarily yield the most interpretable annotation. Interpretability reigns supreme in most SAGA applications. End users find annotations most useful when they have about 5–20 labels for two reasons. First, most can only articulate that many known distinctions between classes of genomic elements. Second, even if one could find meaningful distinctions between a large number of labels, few using the resulting annotations could keep fine distinctions between such a large number of patterns in their working memory. [ 68 ] Even if a statistical approach supported the use of 50 labels, the complexity of such an annotation would make it impractical for most users.


## Annotating multiple cell types

There now exist epigenomics datasets describing hundreds of biological samples ( Figure 3 a). Researchers have correspondingly adapted SAGA methods to work with many samples simultaneously.

We use the term “sample” to refer to some population of cells on which one can perform an epigenomic assay. A sample could correspond to a primary tissue sample, a cell line, cells affected by some perturbation such as drug or disease, or even cells from different species.

The simplest approach for annotating multiple samples involves simply training a separate model on each sample [ 11 ] ( Figure 3 b). The large number of models produced by this approach necessitates using an automated label interpretation process (see “Label interpretation”).

Two categories of approaches aim to share information across samples. The first, “horizontal sharing” or “concatenated” approaches, share information between samples to inform the label-training process. The second, “vertical sharing” or “stacked” approaches, share position-specific information to inform the label assignment of each position.


## Horizontal sharing: emphasizing similarities across samples for learning labels

The simplest way to remove the need for interpreting multiple models is to apply a single model across many samples. To do this, one can treat each sample as referring to separate copies of a longer genome added horizontally after the first one in a “concatenated” approach ( Figure 3 b). One performs concatenated training and inference little differently than if the data from different samples pertained to different chromosomes in the same genome. Because all samples share a single concatenated model, researchers need only perform post-processing interpretation once.

The concatenated approach has wide usage [ 69 , 6 , 7 ] , but has two downsides. First, concatenated SAGA requires that every sample has data from the same assays. In practice, this criterion often does not hold true. This means that—unless these assays are imputed or treated as missing (see “Vertical sharing: emphasizing similarities across samples in positional information”)—one must exclude data for an assay conducted in even all but one samples. In a simple concatenated approach, one cannot annotate a sample which lacks even one dataset present in the others.

Second, data from different samples can have artifactual differences or batch effects. Applying the same model across multiple cell types assumes that all datasets from the same assay type have similar statistical properties. This can result in label distributions to vary wildly across samples and biologically implausible sample-specific labels. Data normalization can help abate the problem of different statistical properties between samples, but usually does so incompletely. This problem is particularly significant when using continuous signal. In contrast, binarizing the data (see “Input data”) can cover up some experimental biases.

One might expect that concatenated annotation would benefit training by increasing the amount of training data. As it turns out, multiplying the amount of training data does not significantly aid the training process, as the types of labels vary little across samples. Most complex eukaryotic organisms studied with SAGA have very large genomes, and just one sample provides plenty of training data. In fact, for computational efficiency, researchers often train on just a fraction of the available samples [ 7 ] , a fraction of the genome from a given sample [ 9 ] or both.


## Vertical sharing: emphasizing similarities across samples in positional information

Another class of multi-sample SAGA methods shares position-specific information across samples as part of the annotation process. These methods take advantage of the non-independence of biological activity across samples at a genomic position. For example, if a given position has an active enhancer label in many samples, it is more likely to act as an active enhancer in a new sample.

The simplest type of vertical sharing approach learns a model on data from all samples jointly ( Figure 3 b). One can implement this “stacked” approach by adding datasets from all samples vertically into a single combined model. A stacked model captures patterns of activity across multiple cell types. For example, a stacked model, unlike an independent model, can find a label for an enhancer active in cell type A and cell type B but inactive in cell type C.

Although conceptually simple, the stacked approach tends not to work well for more than several cell types. Stacking fails with larger number of cell types because each pattern of activity requires its own label. Therefore, the number of labels must grow exponentially in the number of samples. A simple stacked model that treats all assays as independent also ignores the relationship between assays on the same cell type, or the same assay type on different cell types.

A second approach uses a concatenated model that additionally learns a position-specific preference over the labels for each position. Through this preference, data from one sample can influence inference on another. Two implementations have applied variants of this hybrid horizontal-vertical sharing approach. First, TreeHMM [ 12 ] uses a cellular lineage tree as part of its input. For each genomic position, TreeHMM models statistical dependency between the label of a parent cell type and that of a child cell type. Second, IDEAS [ 18 ] uses a similar approach to TreeHMM, but dynamically identifies groups of related samples rather than using a fixed developmental structure. The IDEAS model allows these sample groups to vary across positions, which allows for different relationships between samples in different genomic regions.

A third approach for vertical sharing uses a pairwise prior to transfer position-specific information between cell types [ 17 , 3 ] . In other words, if position i i and position j j received the same label in many other samples, then they should be more likely to receive the same label in an additional sample. In contrast to the other methods in this section, the pairwise prior approach does not require the use of concatenated annotation. Therefore, the pairwise approach has the advantage of not requiring the same available data in all cell types.

A fourth approach imputes missing datasets in the target cell type, then applies any of the above annotation methods to the imputed data [ 50 ] . Imputation provides three advantages. First, it ensures that all target cell types have the same set of datasets. Second, one can conduct imputation entirely as a preprocessing step, allowing the use of any SAGA method afterward. Third, the imputation process can normalize some artifactual differences between datasets, making concatenated annotation more appropriate.

Vertical sharing approaches have the downside that one cannot understand the annotation of each sample in isolation. This arises from the influence on label assignments in one sample by data from other samples. In particular, vertical sharing tends to mask differences between samples. For example, if some position has an enhancer label in many samples, vertical sharing approaches will annotate that position as an enhancer in a target cell type too, even with no enhancer-related data in the target cell type.


## Using and visualizing SAGA annotations

A number of resources can aid in the application of SAGA algorithms and annotations. Reference annotations exist for many cell types ( Table 2 ). These obviate the need for a user of the annotation to actually run \@iaci SAGA SAGA method. Alternatively, if the user must run \@iaci SAGA SAGA algorithm on their own data, standardized protocols describe how to perform this process [ 70 , 8 ] .

Most users of SAGA annotations view them through one of three visualization strategies. The first, and most common, strategy displays individual annotations as individual rows or “tracks” on a genome browser ( Figure 4 a). In each row, the browser displays the segments of that annotation for a region of one chromosome, usually indicating the label by color. Popular genome browsers for displaying segmentations include the UCSC ( UCSC ) Genome Browser [ 73 ] , the WashU ( WashU ) Epigenome Browser [ 74 ] , and Ensembl [ 75 ] .

A second visualization strategy integrates annotations of all samples ( Figure 4 b). This visualization stacks all labels for a given position on top of one another and scales the vertical axis by an estimate of functional importance of that position. Two methods can estimate this importance: Epilogos ( https://epilogos.altius.org/ ), which emphasizes rare activity, and the CAAS , which measures activity that is correlated with evolutionary conservation [ 11 ] .

A third visualization strategy aggregates information about each label across the entire genome. This shows the enrichment of each label at positions of known significance, such as gene components ( Figure 4 c) or curated enhancers. Tools such as Segtools [ 76 ] and deepTools [ 77 ] can create these visualizations.

SAGA annotations can provide valuable reference datasets to other analyses and tools. The assignment of one and only one label from a small set to every mappable part of the genome greatly eases downstream analyses. SAGA annotations summarize genomic activity in a much simpler way than the individual input datasets, and even than processed versions of the input datasets such as peak calls.

Most SAGA annotations are in the tab-delimited BED ( BED ) format ( https://genome.ucsc.edu/FAQ/FAQformat.html#format1 ). This makes it easy to remix SAGA annotations with other datasets using powerful software such as BEDTools [ 78 ] . SAGA annotations form building blocks for methods for integrative analysis of genomic data such as CADD [ 79 ] .


## Conclusions and outlook for future work

SAGA methods provide a powerful and flexible tool for analyzing genomic datasets. These methods promise to continue to play an important role as researchers generate more datasets. Despite the large existing literature, future work could still address many challenges.

Nucleosome-scale annotations ( 100 bp to 1000 bp 100\text{\,}\mathrm{bp}1000\text{\,}\mathrm{bp} segments) of histone modifications have wide usage. While annotations of different data types or at different length scales exist, they are less widely used. Currently, there exist reference domain annotations with segments of length 1 × 10 5 bp to 1 × 10 6 bp 1\text{\times}{10}^{5}\text{\,}\mathrm{bp}1\text{\times}{10}^{6}\text{\,}\mathrm{bp} for only a small number of samples [ 4 , 42 , 80 , 3 ] , and few or no annotations at other scales.

. Genome annotations would improve with better processing and normalization of input datasets. Representations such as fold enrichment used by existing methods seem primitive compared to more rigorous quantification schemes used in RNA-seq analysis such as TPM ( TPM ). One could also improve SAGA preprocessing by more frequently incorporating information from multi-mapping reads [ 81 ] .

Most methods do not report any measure of confidence in their predictions. Two types of confidence would prove useful. First, one would often like to know the level of confidence that a position in some sample has label X and not label Y. Second, in many cases one would like to have confidence in a differential labeling between two samples—that cell type A and cell type B have different labels. Two methods work towards a solution for the second problem [ 82 , 83 ] , but there remains much room for further work.

Existing SAGA methods output a discrete annotation, assigning a single label to each position. In this discrete approach, annotations cannot easily represent varying strength in activity of genomic elements or elements that simultaneously multiple types of activity. A continuous annotation approach analogous to the topic models used for text document classification might address this limitation [ 84 ] .

Existing SAGA methods use data from bulk samples of cells. Increasing availability of data from single-cell assays necessitates the development of methods that can leverage this additional information.

The semantics of genome annotations correspond poorly to the way most molecular biologists conceptualize genomic elements. Most existing annotations are cell-type-specific—the annotation states that a given locus acts as an active enhancer in cell type A. In contrast, researchers often state that a given locus “is an enhancer”.

In contrast, other annotations—such of those of protein-coding genes—serve as a pan-cell-type characterization. Each gene has a fixed location, and only its expression varies across samples.

There exists a need for pan-cell-type epigenome annotations. Such an annotation would define fixed intervals for regulatory elements such as promoters, enhancers, and insulators, and it would specify in which samples each element is active. Specifically targeting this task in the SAGA model could improve results over pan-cell-type annotations assembled from multiple cell-type-specific SAGA models [ 11 ] .


## Author contributions

Conceptualization, M.W.L. and M.M.H.; Funding acquisition, M.M.H.; Investigation, M.W.L., R.C.W.C., and M.M.H.; Visualization, M.W.L. and R.C.W.C.; Writing — original draft, M.W.L., R.C.W.C., and M.M.H.; Writing — review & editing, M.W.L. and M.M.H.


## Acknowledgments

This work was supported by the Natural Sciences and Engineering Research Council of Canada (RGPIN-2015-03948 to M.M.H.)


## Competing interests

The authors declare no competing interests.


## Acronyms


## References