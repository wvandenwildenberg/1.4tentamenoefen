# Report

Answer the following questions based on the analyses performed in the notebook and the notes you made. Explain your reasoning clearly. No Python code is required.

## Background and key results

The farmer's peat parcel is observed with two independent techniques: **InSAR** (average height change of the whole parcel, every 6 days, $\sigma_{\text{InSAR}} = 3$ mm) and an **extensometer** (height change at one point, daily, $\sigma_{\text{ext}} = 8$ mm). Two functional models were estimated with BLUE:

- **Model 1** (offset + velocity): $d(t) = d_0 + v\,t$, with $t$ in years since 1 January 2020.
- **Model 2** (weather model): $d(t) = d_0 + x_I\,D(t) + k\,S_{10}(t)$, with $D(t)$ the number of dry days and $S_{10}(t)$ the water surplus with $\tau = 10$ days.

You may use the following results obtained in the notebook (estimate $\pm$ standard deviation):

| | InSAR ($m = 145$) | Extensometer ($m = 1461$) |
|---|---|---|
| **Model 1:** $\hat{d}_0$ [mm] | $6.0 \pm 0.5$ | $2.4 \pm 0.4$ |
| **Model 1:** $\hat{v}$ [mm/yr] | $-5.37 \pm 0.21$ | $-7.95 \pm 0.18$ |
| **Model 1:** std of residuals [mm] | $11.5$ | $16.9$ |
| **Model 2:** $\hat{d}_0$ [mm] | $7.7 \pm 0.7$ | $5.8 \pm 0.6$ |
| **Model 2:** $\hat{x}_I$ [mm/dry day] | $-0.0422 \pm 0.0016$ | $-0.0613 \pm 0.0014$ |
| **Model 2:** $\hat{k}$ [-] | $0.463 \pm 0.012$ | $0.684 \pm 0.011$ |
| **Model 2:** std of residuals [mm] | $5.7$ | $9.9$ |

On average, the parcel has $N_{\text{dry}} \approx 131$ dry days per year in the observation period (2020–2023).

---

## Question 1: Functional and stochastic model

**a)** For Model 1, write the observation equations in matrix form $\mathbb{E}(Y) = A\,x$ (no numerical values needed, use $t_1, t_2, \dots$). You do not need to write out the whole matrix. State the units of the unknowns.


**b)** Sketch the structure of the covariance matrix $\Sigma_Y$ for the InSAR observations. State the dimension of the matrix. You do not need to write out the whole matrix.

How is the assumption that the observations are independent included?


**c)** Write down the BLU estimator $\hat{X}$ and its covariance matrix $\Sigma_{\hat{X}}$. BLUE is a special case of weighted least-squares. Which weight matrix $W$ does BLUE use, and why does a more precise observation receive more weight?


---

## Question 2: Results of Model 1 (offset + velocity)


**a)** Precision of the observations and of the estimates:
- Which sensor gives the more precise individual observations?
- Which sensor gives the more precise estimate of the velocity $v$?
- Does this make sense? Explain the relation between the precision of an estimated parameter and the number of observations. Use the redundancy of both datasets in your answer.


**b)** Compare the estimated velocities of InSAR and the extensometer. Do you think the difference is significant, given their standard deviations? Give a possible explanation.


**c)** The figure below shows the observations, the fitted Model 1 and the 98% confidence interval of $\hat{Y}$ for both sensors.

![Model 1: observations, fitted model and 98% confidence interval](https://github.com/TUDelft-MUDE/source-files/raw/main/file/GA1.7/GA1.7_model1_fit.png)

The 98% confidence interval of $\hat{Y}$ is very narrow, but many observations lie far outside it. Does this mean the confidence interval is computed wrongly? Explain what the confidence interval of $\hat{Y}$ represents, and why this is not a contradiction.


**d)** Using the figure in 2c, sketch the residuals of Model 1 for the extensometer as a function of time. The standard deviation of the extensometer residuals is $16.9$ mm, while $\sigma_{\text{ext}} = 8$ mm. What does this tell you about Model 1?


---

## Question 3: Model 2 (weather model)


**a)** Explain the physical meaning and the sign of the estimated parameters $\hat{x}_I$ and $\hat{k}$.


**b)** Convert $\hat{x}_I$ for InSAR to a subsidence rate in mm/yr and compare it with the velocity $\hat{v}$ of Model 1. Also convert the standard deviation. What is the difference in interpretation between the two models?


---

## Question 4: Model comparison and advice to the farmer

The figure below shows the residuals of Model 2 for the extensometer as a function of time (left) and the histogram of the normalized residuals $\hat{\epsilon}/\sigma$ together with the standard normal distribution $N(0,1)$ (right).

![Extensometer Model 2: residuals and normalized residuals](https://github.com/TUDelft-MUDE/source-files/raw/main/file/GA1.7/GA1.7_model2_residuals.png)

**a)** Compare the residuals of Model 2 in the figure with your sketch of the Model 1 residuals from Question 2d. Look at the size of the residuals (see also the std of the residuals in the table) and the pattern in time. Explain why Model 2 describes the data better.


**b)** Model 2 is better, but is it "correct"? Use the figure (residuals and histogram) and the table (**compare the std of the residuals with $\sigma$ for both sensors**) to argue whether the model is complete, and suggest one way to improve it.



**c)** Write a short advice (3–4 sentences) to the farmer: is his parcel sinking, how fast, and what is driving it? Which dataset would you use to describe the parcel as a whole?


---

## How did things go? (Optional)

Use this space to let us know if you ran into any challenges while working on this GA, and if you have any feedback to report.

> By Lina Hagenah and Isabel Slingerland, Delft University of Technology. CC BY 4.0, more info [on the Credits page of Workbook](https://mude.citg.tudelft.nl/workbook-2026/credits.html).

```{custom_download_link} ./all_files_GA_1_7.zip
:text: ".zip assignment"
:replace_default: "True"
```
