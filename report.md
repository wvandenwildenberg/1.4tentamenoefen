# Report

Answer the following questions based on the analyses performed in the notebook and the notes you made. Explain your reasoning clearly. No Python code is required.

## Background

The farmer's peat parcel is observed with **InSAR** ($m = 145$, $\sigma_{\text{InSAR}} = 3$ mm, average of the whole parcel) and an **extensometer** ($m = 1461$, $\sigma_{\text{ext}} = 8$ mm, one point in the parcel). The observations are independent and normally distributed. Last week (GA1.7) we fixed the memory timescale of the soil at $\tau = 10$ days. This week $\tau$ is estimated as an extra unknown:

$$
q(x) = d_0 + x_I D(t) + k S_\tau(t),
\qquad
S_i = a S_{i-1} + (P_i - E_i), \quad a = e^{-1/\tau}, \quad S_{-1} = 0,
$$

with unknowns $x = [d_0,\ x_I,\ k,\ \tau]^T$. The model is solved with Gauss-Newton, starting from $x_{[0]} = [5\ \text{mm},\ -0.04\ \text{mm/dry day},\ 0.4,\ 20\ \text{days}]$.

You may use the following results of the overall model test (OMT) for the model with $\tau$ estimated, obtained in the notebook with $\alpha = 0.05$:

| | $T$ | $k_\alpha$ | $r$ | std of residuals [mm] |
|---|---|---|---|---|
| InSAR | $113.1$ | $169.7$ | $141$ | $2.65$ |
| Extensometer | $1516.5$ | $1546.9$ | $1457$ | $8.15$ |

---

## Question 1: Non-linear model and linearization

**a)** The model is linear in $d_0$, $x_I$ and $k$, but non-linear in $\tau$. Explain why, and why we can no longer write the model as $\mathbb{E}(Y) = A x$ and solve it directly with BLUE.


**b)** Gauss-Newton uses the Jacobian matrix $J$ as the design matrix $A$.
- Sketch the structure of $J$ for this model (e.g., show what is on the first and last rows): what does each column contain? You may write $\dfrac{\partial S_\tau}{\partial \tau}$ without working it out.
- Which columns of $J$ change from one Gauss-Newton iteration to the next? Explain why.


---

## Question 2: Initial values and convergence

**a)** Why does Gauss-Newton need initial values, and why is it important that they are reasonably good? Give two things that can go wrong with bad initial values.


**b)** The figure shows the convergence of the four parameters for InSAR.

![Convergence of Gauss-Newton for InSAR](https://github.com/TUDelft-MUDE/source-files/raw/main/file/GA1.8/convergence_insar.png)

Describe the convergence. How many iterations are needed?


---

## Question 3: Overall model test

**a)** Formulate the null hypothesis of the overall model test (OMT). Give the test statistic $T$ and its distribution under $H_0$. When is $H_0$ rejected?


**b)** Sketch the PDF of the test statistic for InSAR with $\tau$ estimated ($r = 141$). Indicate in your sketch:

- the critical value $k_\alpha$ and the rejection region ($\alpha = 0.05$);
- the test statistic $T$ for InSAR.


**c)** Interpret the OMT results for both sensors. Compare $T$ with $k_\alpha$ and with the redundancy $r$. Does accepting $H_0$ prove that the model is correct?


---

## Question 4: Comparing models

**a)** This week we added one unknown ($\tau$) to last week's model. In general, how does adding unknowns affect the redundancy $r$, the test statistic $T$ and the critical value $k_\alpha$? Explain why.



**b)** Assume that last week's model ($\tau$ fixed at 10 days) was tested first and rejected by the OMT. Which other test could you use to check whether the new model ($\tau$ estimated) is significantly better? Give its test statistic.


---

## How did things go? (Optional)

Use this space to let us know if you ran into any challenges while working on this GA, and if you have any feedback to report.

> By Lina Hagenah, Delft University of Technology. CC BY 4.0, more info [on the Credits page of Workbook](https://mude.citg.tudelft.nl/workbook-2026/credits.html).

```{custom_download_link} ./all_files_GA_1_8.zip
:text: ".zip assignment"
:replace_default: "True"
```
