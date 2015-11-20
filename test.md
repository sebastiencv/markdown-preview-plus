* Objective : learn statistic as a language [Intro].
* Target : conceptual approach on statistics (why instead of how) [Intro].


# Short notations


|**Expectation (μ)**<br>mean |$E[\mathbf{x}] = \frac{x_1p_1 + x_2p_2 + \dotsb + x_kp_k}{p_1 + p_2 + \dotsb + p_k}$, if uniform : $= \frac{1}{N\star}\sum_i{x_i}$ |
|-|-|
|**SD (σ)**<br>Standard Deviation |$\sigma_x = \sqrt{E[(\mathbf{x}-\mu_x)^2]} = \sqrt{\frac{1}{N\star}\sum_i{(x_i-\mu_x)^2}}$ |
|**Z-score**<br>Std unit of measurement (like if μ=0, σ=1) |$\mathbf{z}_x = \frac{\mathbf{x}-\mu_x}{\sigma_x}$ *: is a centered/normalized vector of length* $\sqrt{N\star}$ |
|**COV**<br>Covariance |$\begin{aligned} \sigma(\mathbf{x},\mathbf{y}) &= E[(\mathbf{x}-\mu_x)^T(\mathbf{y}-\mu_y)] = E[\mathbf{x}^T\mathbf{y}]-E[\mathbf{x}]E[\mathbf{y}]\\ &= \frac{1}{N\star}\sum_i{(x_i-\mu_x)(y_i-\mu_y)}\\ \sigma(\mathbf{x},\mathbf{x}) &= \sigma_x^2 \end{aligned}$ |
|**r (ρ)**<br>Correlation coefficient<br>(Pearson product-moment correlation coefficient)<br>Correlation is standardized (range [-1, 1]) of COV<br>Rem : bad for y = x^2<sup>ρ is bad for non-linear relations</sup>  |$\rho =\frac{\text{degree of which }\mathbf{x}\text{ and }\mathbf{y}\text{ vary together}}{\text{degree of which }\mathbf{x}\text{ and }\mathbf{x}\text{ vary independently}}$<img src="media/ai/rs/800px-correlation_examples.png" style="border: 0px none; margin: 0px;0px 0px 1.5em;width: 200px;float: right;"><br><br>$\rho = \frac{\sigma(\mathbf{x},\mathbf{y})}{\sigma_x \sigma_y} = \frac{1}{N\star}\sum_i{(\frac{x_i-\mu_x}{\sigma_x})(\frac{y_i-\mu_y}{\sigma_y})} = \frac{1}{N\star}\sum_i{z_{xi}z_{yi}}$<br>*= cos (angle btw z<sub>x</sub> and z<sub>y</sub>)* |
|**SE**<br>Standard Error<br>Std deviation of the distribution-of-sample-means |$SE_x = \frac{\sigma_{population}}{\sqrt{N}} = \frac{\sqrt{\sum_i{(x_i-\mu_{population})^2}}}{N}$ |
|**P(E)**<br>Probability of an event (E) happening |$P(E) = \frac{\text{# of ways E can be attained}}{\text{total # of possible outcomes}}$ |
|**Deviation** |$D_x = \mathbf{x} - \mu_x$ |
|**SS**<br>sum of squared deviation |$SS_x = \sum_i{(x_i-\mu_x)^2}$ |
|**MS**<br>Mean squares |$MS_x = \frac{\sum_i{(x_i-\mu_x)^2}}{N}$ |
|**SP**<br>sum of cross-products |$SP_{xy} = \sum_i{(x_i-\mu_x)(y_i-\mu_y)}$ |



### Notions


* Percentile rank :
  * Percentage of scores below a given score.


* Denominator $n\star$ :
  * Divide by N : for descriptive purpose
  * Divide by (N-1) : for inferential purpose

# Correlation vs. causality


## Randomized contrôle experiences : causality



* They allow for strong **claims about causality** (link dependent variables / independent variables) : « why stuff happens ? predict-prevent ».
* Conditions : true independent variables, random and representative samples
* Definitions :
  * **Population** : the entire collection of case, target of the generalization.
  * **Sample** : subset of the population.
  * **Parameter** : a num measure that describes a characteristics of a population.
  * **Statistic** : a num measure that describes a characteristics of a sample.
  * **Descriptive statistics** : describe, summarize, organize and simplify sample data.
  * **Inferential statistics** : techniques for generalizations from statistics to parameters.
  * **Independent variable** : variable manipulated by the experimenter (receive vaccine or placebo).
  * **Dependent variable** : predicted variable (element of the world) in function of independent variable (recover or not).


## Observational studies : correlation : patterns/structures/models

<img src="media//screen_shot_2012-10-05_at_11.45.49.png" style="border: 0px none; margin: 0px;0px 0px 1.5em;width: 200px;float: right;"><img src="media//screen_shot_2012-10-05_at_11.43.57.png" style="border: 0px none; margin: 0px;0px 0px 1.5em;width: 200px;float: right;">

* Study vs. experiment (random) : **nothing is manipulated** (independent variables), target patterns of correlations => models.
* Find factors.
* Correlation is not causality.
* **Quasi-independant variable** : not choosen by the experimentator => is a correlation study (not causality experiment).
* Compute correlations (r).
* Conditions/assumption for correlation validity :
  1. Normal distribution of X and Y (check : plot histograms or use `describe`).
  1. Their is a linear relationship between X and Y (check : plot scatterplots, plot histogram of residuals).
  1. Homoskedasticity (check : examine scatterplots, plot histogram of residuals).
    * In a scatterplot, the distance (residual) between a dot and the regression line reflects the amount of prediction error.


# Inferential vs. descriptive statistics



## Descriptive statistics


### Histograms


* Histograms show an entire distribution (not the summary : e.g. retaining the mean, forgetting the deviation).


### Summary statistics


* The four moments of the mean :
  1. Central tendency :
    * measure de central point of the distribution,
    * e.g. **mean**, **median**, **mode** (score that occurs most, peak).
    * Median is better than mean in case of high skew.
  1. Variability,
    * e.g. standard deviation (SD), and variation (SD^2 = MS, mean squares).
  1. Skew : ok if < 3 (using the `describe` function in R).
  1. Kurtosis


## Inferential statistics


* Probability + assume normal distribution => Inferential statistics
  * e.g. suppose X selected at random, $P(X > M_x) =  0.5$



# Measurement


* Quality of measurement :
  1. Reliability and validity
  1. Sampling


## Reliability


* *Repetable*.
* Checked via test theory :
  * Computed value are not perfect : contains : **bias** and **errors** => try to estimate reliability.
* Three methods to compute reliability :
  1. **Test / retest** : measure twice, then run **correlation** between X1 and X2 (but this not reveal bias).
    * Very good correlation : **0.9-0.95**.
    * How to structure re-test data :
      * Typical : add new column, but in R, it is better to **add new rows**.
  1. **Parallel tests** : use another method (temperature with wand and thermometer) : reveal the bias.
  1. **Inter-item estimates** : cheaper : split the sample in two, then compute the correlation.
* Reliability of a correlation :
  * Check via **NHST** (null hypothesis significant testing)


## NHST (null hypothesis significant testing)



* H<sub>0</sub> : assume-guess null hypothesis, no correlation (r=0 or B=0).
  * Then compute probability of observing data $D$ with these characteristics, given H<sub>0</sub> is true :
  * $p=P(D¦H_0)$ : this is a conditional probability
  * if `p<α`, the reject H<sub>0</sub>, else retain H<sub>0</sub>.
* H<sub>A</sub> : alternative hypothesis : they are correlation (r>0 or B>0).

| |  Experimental Decision  ||
|-|-|-|
| | Retain H<sub>0</sub> | Reject H<sub>0</sub> |
| H<sub>0</sub> is true |Correct Decision |Type I error (false alarm) |
| H<sub>0</sub> is false |Type II error (miss) |Correct Decision  |

## Construct validity


* *Valider un construct (**fiction**, parfois régulatrice) : induction.*
* What is a construct : an objet not directly observable, e.g. intelligence *: an explanation*.
* Operationalize a construct : How to make observable, quantifiable : e.g. intelligence test. *Tester des conséquences du construct*.
  1. Content validity : is this test possible for the population ? *Ce qu'on va mesurer est-il bien une conséquence possible du construct?*
  1. Convergent validity : does the test correlate with other established measure (reading tests...) ? *Corrélation / cohérence entre conséquences du même construct, converger vers lui.*
  1. Divergence validity : does the test diverge with other abilities measures (wealth...) ? *Divergence si mesure d'autres construct : différentiation*.
  1. Nomological validity : is linked to higher principles, rules. *Cohérent avec des principes généraux.*


## Sampling


* How to estimate the sampling error ?
  * Depends on the sample size, relative to population size
  * Depends on the population variability (SD).
* SE (Standard Error) is the estimate of the amount of sampling error : $SE_x = \frac{\sqrt{\sum{(X-M_x)^2}}}{N}$
  * Comes from : « Distribution of sample means » :
    * If we **repeat** sampling, and compute the mean on each sample and draw an histogram of that mean : the deviation of this histogram will be smaller if the sample is big (N>>) => source of the SE.
    * The variance of the distribution-of-sample-means is less than de distribution of the population of individuals : $SD^2_{dosm}=\frac{SD^2_{population}}{N} = SE^2$
  * Hypothesis :
    1. The mean of the distribution-of-sample-means = mean of the population
    1. The distribution-of-sample-means is normal distribution (N >+ 30 or shape of the population is normal).
    1. Mixing SD<sub>population</sub> and SD<sub>sample</sub> (?).


# Regression


* A statistical analysis used to predict scores on an **outcome variable** (Y : dep var), based on scores on one or more **predictor variables** (X : indep var).
  * Not just regressions, since X may be composed of more than one variable.
* $\hat{Y} = B_0 + B_1 X$, $Y-\hat{Y} = e$, « e » is the prediction error / residual (distance in the scatterplot from a point to the regression line).
  * $B = r\frac{SD_y}{SDx}$
  * With normalization : $\beta = r$ (β is the Standardized regression coefficient).
* The regression model is used to "model" / predict future behavior . A model is an equation.
  * Regression goals is to produce a good model (choose variables, choose equations type).
  * Evaluation : plot histogram of residuals, or scatterplot between X and e => if their is a relation, the homoscedasticity => maybe need to add a predictor variable ?


## Multiple regression


* $\hat{Y} = B_0 + \sum_k B_k X_k$

