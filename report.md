# Report

_Complete this report by hand, using only the handwritten reference notes you prepared during the setup notebook. No laptop, internet, AI, or other resources may be used during the written hour._

## Questions

### Question 1 — Method of moments

#### 1.1

Briefly explain which distributions you fit to $q$ and $h$, and why.

#### 1.2

Consider a Gumbel distribution for the discharge $q$, with probability density function

$$f_Q(q)=\frac{1}{\beta}\exp\left[-\frac{q-\mu}{\beta}-\exp\left(-\frac{q-\mu}{\beta}\right)\right],\qquad \beta>0.$$

For this distribution,

$$
E[Q] = \mu + \gamma\beta
$$

and

$$
\text{Var}(Q) = \frac{\pi^2}{6}\beta^2,
$$

where $\gamma\approx0.5772$ is the Euler--Mascheroni constant.

Using the mean and standard deviation of $q$ from your handwritten reference notes:

1. Apply the method of moments by equating the theoretical mean and variance above to the sample mean and variance from your notes. Show your derivation.
2. Compare your result with the fitted parameter values from the notebook.
3. Briefly explain why the two estimation methods do not have to give exactly the same parameter values.


**Solution**

**1.1**

For $h$, between a lognormal and a uniform pdf, the <b>Lognormal distribution</b> is the more plausible of the two candidates. The observed depths are strongly concentrated around approximately $3.4$ m rather than being spread uniformly between their minimum and maximum values. The observations also have a modest positive skewness, which a Lognormal distribution can represent whereas a Uniform distribution cannot.

For $q$, between a Gaussian and a Gumbel, the <b>Gumbel distribution</b> is the more plausible candidate. The discharge observations have a pronounced positive skewness and a clear right tail. A Gaussian distribution is symmetric, whereas the right-skewed Gumbel distribution can reproduce right tails.

**1.2**

For a Gumbel distribution,

$$
\beta = \frac{\sqrt{6}}{\pi}\sigma
$$

and

$$
\mu = \overline{q}-\gamma\beta,
$$

where $\gamma\approx0.5772$ is the Euler–Mascheroni constant.

Using $\overline{q}\approx8.657$ m$^3$/s and $s_q\approx2.592$ m$^3$/s,

$$
\beta \approx \frac{\sqrt{6}}{\pi}(2.592) \approx 2.021\ \mathrm{m^3/s},
$$

and

$$
\mu \approx 8.657-0.5772(2.021) \approx 7.490\ \mathrm{m^3/s}.
$$

If we compare these values with the MLE location and scale copied from the notebook, we note that the estimates should be of similar magnitude, but they need not be identical: method of moments and maximum likelihood use different criteria to estimate the parameters. Agreement for this dataset does not imply that the two methods will always give similar estimates.

> **General feedback**
>
> There was some confusion generally about the goal of the 2 methods: a fitted distribution is defined by its parameters, which are calculated differently using MOM vs MLE; the fitted distributions themselves are not different in shape, etc.


---

### Question 2 — Goodness of fit

During Section 4 of the setup notebook you assessed the fitted distributions for $h$ and $q$ graphically with the help of exceedance probability plots. Sketch these distributions qualitatively.

For each variable, qualitatively describe how well your function fits the data. How is the fit in the tails, and what might be the consequences of differences in the tail behaviour?

Support your answer using specific evidence from the graphical checks recorded in your handwritten notes.


**Solution**

For $h$ (Lognormal) and  $q$ (Gumbel), both distributions have a reasonable fit over most of the curve, with small deviations (sometimes over-, sometimes under-estimating the empirical exceedance probability).

At the most extreme observed values, both fitted exceedance curves lie above the empirical curves, so the models assign more probability to values at or beyond those extremes.

> **General feedback**
>
> In submissions the general plots and outcomes were correct but the interpretation was lacking, for example saying just "the fit was poor at the tails" instead of interpreting over/under-estimation of extremes


### Question 3 — Contingency probabilities

Choose **one** of the two raw contingency tables in your handwritten reference notes, **copy the raw data table into this report**, and use the same table throughout this question. Clearly state which variable pair you selected.

#### 3.1

Convert the raw counts in your table into **joint probabilities**. Show your calculation for one cell.

#### 3.2

Determine the **marginal probability distribution** of each variable. Show your calculation for one marginal value.

#### 3.3

Choose one category of one of the variables. Among the observations in that category, determine the **probability distribution of the other variable**. Show the calculations of how you obtained the probabilities and explain in words what this conditional distribution represents.

#### 3.4

Select one cell from the conditional distribution in part (c). Now reverse the conditioning direction and calculate the corresponding conditional probability for that cell. Compare the two conditional probabilities and explain why they are generally different. Under what conditions would they be identical?


**Solution**

The numerical answers depend on the contingency table selected by the group.

For a table containing $n$ observations, each joint probability is the corresponding cell count divided by $n$:

$$
P(A_i,B_j)=\frac{n_{ij}}{n}.
$$

The marginal distributions are obtained by summing the joint probabilities over the other variable, or equivalently by dividing the row and column totals by $n$.

For part (c), choosing a category $B$ means restricting attention to the observations in that category and normalizing the corresponding row or column. The resulting entries are

$$
P(A_i\mid B)=\frac{P(A_i,B)}{P(B)}.
$$

Their sum should equal 1. The verbal interpretation must make the conditioning direction clear: these are probabilities **among the observations satisfying $B$**, or **while keeping $B$ fixed**.

For a selected category $A$, reversing the conditioning gives

$$
P(B\mid A)=\frac{P(A,B)}{P(A)}.
$$

The joint numerator is the same, but the denominator — and therefore the reference group — has changed. The two probabilities are consequently generally different.

If $P(A,B)>0$, then

$$
\frac{P(A,B)}{P(B)}=\frac{P(A,B)}{P(A)}
$$

holds exactly when

$$
P(A)=P(B).
$$


---

### Question 4 — Cumulative probability

Consider **one of the two marginal distributions** from the contingency table you used in Question 3.

Would constructing a cumulative distribution function (CDF) for this variable give a meaningful probability description?

Explain what property of a variable determines whether cumulative probabilities such as

$$
P(X\leq x)
$$

have a useful interpretation.


**Solution**

For the nominal categorical variables in the questionnaire, a CDF is generally not meaningful.

A CDF is defined as

$$
F_X(x)=P(X\leq x),
$$

so the possible outcomes must have a meaningful ordering. This is true for numerical variables and can also be true for ordinal categorical variables.

For nominal categories there is no natural meaning to one category being "less than" another. Any cumulative probability would therefore depend on an arbitrary ordering of the categories rather than on a meaningful property of the variable.

> **General feedback**
>
> Many groups said variables need to be numerical or continuous to create CDFs which is not true: categorical variables which are ordered (ordinal variables) can still be used to create meaningful CDFs.


---

### Question 5 — Modelling assumptions

Compare the two correlation coefficients in your handwritten reference notes, $\rho_{obs}$ and $\rho_{sim}$.

#### 5.1
What do these results tell you about the assumption made when $h$ and $q$ were sampled in the Monte Carlo simulation?

#### 5.2
Does your Monte Carlo simulation generate realistic samples for the simulation of $u=\frac{q}{wh}$? Justify your choice.


**Solution**

**a.** The independently generated samples should have a correlation close to zero, because the simulation draws $h$ and $q$ independently. The paired observations show a clear non-zero relationship between water depth and discharge. The comparison therefore indicates that independence does not reproduce an important feature of the observed joint behaviour.

**b.** No, not always. Both variables should be positively correlated. However, since $q$ and $h$ were sampled independently, the sampling can create combinations of high $q$ and low $h$, or vice versa, which occur more readily under independent sampling than suggested by the observed joint relationship.


---

### Last Question: How did things go? (Optional)

_Use this space to let us know if you ran into any challenges while working on this GA, and if you have any feedback to report._

**End of file.**

> By Max Ramgraber, Patricia Mares Nasarre and Robert Lanzafame, Delft University of Technology. CC BY 4.0, more info [on the Credits page of Workbook](https://mude.citg.tudelft.nl/workbook-2026/credits.html).


```{custom_download_link} ./all_files_GA_1_4.zip
:text: ".zip assignment"
:replace_default: "True"
```
