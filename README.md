# algorithm-notes

* [DTW](#dynamic-time-warping)
* [GPR](#gaussian-process-regression)
* [State Space Model](#state-space-model)
* [Knowledge Distillation](#knowledge-distillation)

### Dynamic Time Warping

* One of the most used measure of the similarity between two time series
* **Optimal global alignment** between two time series, exploiting temporal distortions between them

Distance Matrix

<p align=center>
<img src=https://sunny73.github.io/2018/11/07/dtw%E7%AE%97%E6%B3%95/1.png width=400>
<p/>

<p align=center>
<img src=./dtw1.JPG width=600>
<p/>

<p align=center>
<img src=./dtw2.JPG width=600>
<p/>

### Gaussian Process Regression

Normal distribution --> Multivariate normal distribution --> Gaussian process

Dot products measure similarity:
* [1,0] * [[1],[0]] = 1
* [1,0] * [[0],[1]] = 0

To get predictions at unseen points of interest, x*, the predictive distribution can be calculated by weighting all possible predictions by their calculated posterior distribution:

<p align=center>
<img src=https://miro.medium.com/max/1050/1*Se-i1g57jCoLy4EszR74hg.png width=400>
<p/>

**Gaussian process regression** is nonparametric (i.e. not limited by a functional form), so rather than calculating the probability distribution of parameters of a specific function, GPR calculates the probability distribution over all admissible functions that fit the data.

* Parametric models assume that the data distribution can be modeled in terms of a set of finite number of parameters.
* If the number of parameters of a model grows with the size of observed dataset, it’s a non-parametric model. A non-parametric model does not imply that there are no parameters, but rather infinite parameters.

A Gaussian process is a probability distribution over possible functions that fit a set of points. A Gaussian processes regression model provides uncertainty estimations together with prediction values. The prior knowledge of the form of functions can be integrated by using kernel functions.

<p align=center>
<img src=https://production-media.paperswithcode.com/methods/Screen_Shot_2020-05-24_at_3.44.34_PM.png width=300>
<p/>

### State Space Model

* States (e.g. position)
* Derivatives of States (e.g. speed, acceleration)
* Speed can be influenced by both the position (i.e. x) and external energy/inputs (i.e. u)

Linear Time-Invariant system
* State equation
* Output equation

> State variables: minimum set of variables that fully describe the system

### Knowledge Distillation

Definition: extract information from the big model or ensamble model to a new simpler with less parameters while removing the not needed information

Why Softmax:
* Desire a probability distribution as output --> ground truth is one hot encoding
* Exponential --> all entries are positive
* Normalization --> add to 1

Softmax tends to hide the relative similarity between the other classes.

Add a parameter **T** (called temperature) to smooth the probability distribution, the higher T, the smoother. If we make the values of logits smaller before passing them to the softmax then we may retain the relativeness.

<p align=center>
<img src=https://miro.medium.com/max/620/1*kISX_umTkEvg7cM6dAyTtQ.png width=150>
<p/>

* Smooth logits = Soft labels (distilled network)
* Regular vanilla = Hard labels

<p align=center>
<img src=https://i.stack.imgur.com/uOrit.png>
<p/>

