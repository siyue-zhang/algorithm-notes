# algorithm-notes

* [DTW](#dynamic-time-warping)
* [GPR](#gaussian-process-regression)

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
