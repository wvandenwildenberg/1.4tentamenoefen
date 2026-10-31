# Report

Submit **one set of handwritten answers per group** at 12:30. 

Computers, phones, online resources and AI tools are not permitted. You may use only the handwritten notes prepared earlier in the session. **Show the formulas and reasoning that support your answers; numerical answers without an explanation will not receive full credit.**

## Given model and numerical reference values

The simplified Stefan model for ice thickness after a cold spell is

$$
H_\mathrm{ice}=q(H_{\mathrm{ice},0},\Delta T)
=\sqrt{\frac{2k_\mathrm{ice}}{\rho_\mathrm{ice}l}\,\Delta T\,\Delta t+H_{\mathrm{ice},0}^2},
\qquad \frac{2k_\mathrm{ice}}{\rho_\mathrm{ice}l}=1.44\times10^{-8}\ \mathrm{m^2/(K\,s)}.
$$

where $H_{\mathrm{ice},0}$ is the initial ice thickness, $\Delta t$ is the duration in seconds, and $\Delta T$ is the temperature deficit relative to the freezing point, in Kelvin. 

Use $\Delta t=5\times24\times3600\ \mathrm{s}$, $\mu_{H_0}=0.20\ \mathrm{m}$, $\sigma_{H_0}=0.03\ \mathrm{m}$, $\mu_{\Delta T}=10\ \mathrm{K}$, and $\sigma_{\Delta T}=4\ \mathrm{K}$. Unless otherwise specified, the two inputs are independent. In the Monte Carlo simulation, negative draws of $\Delta T$ are set to zero (no further ice growth; melting is not modelled). The Taylor approximation is evaluated at the positive input means.

The following are reference results from the notebook ($N=100000$, specified seed). Use them where relevant; answers should focus on the calculations and interpretation.

| Quantity | Independent inputs ($\rho=0$) | Correlated inputs ($\rho=0.5$) |
|:--|--:|--:|
| $q(\mu_{H_0},\mu_{\Delta T})$ [m] | 0.319700 | 0.319700 |
| Second-order Taylor mean $\mu_H$ [m] | 0.318188 | 0.317046 |
| First-order Taylor standard deviation $\sigma_H$ [m] | 0.043206 | 0.050962 |
| Monte Carlo mean [m] | 0.318273 | 0.316976 |
| Monte Carlo sample standard deviation [m] | 0.044155 | 0.052515 |

For the independent-input simulation, the event $H_\mathrm{ice}<0.24\ \mathrm{m}$ has probability **0.04783** according to Monte Carlo and **0.03517** according to the Gaussian CDF with Taylor-propagated moments. Around **0.615%** of temperature-deficit draws were negative and set to zero.

## Part 1 — Mean and variance propagation

**1.1** Derive the first-order partial derivatives $\partial q/\partial H_{\mathrm{ice},0}$ and $\partial q/\partial(\Delta T)$, and state the sign of each derivative at the given means.

**1.2** Derive the second-order partial derivatives $\partial^2q/\partial H_{\mathrm{ice},0}^2$ and $\partial^2q/\partial(\Delta T)^2$. Write the **second-order Taylor approximation of the mean** for independent inputs. Use the reference values to quantify the difference between this mean and $q$ evaluated at the mean inputs.

**1.3** Write the **first-order Taylor variance propagation formula** for independent inputs. Give the resulting standard deviation (in metres) using the provided numerical reference.

**1.4** Explain why evaluating the non-linear model at the input means need not equal the output expectation, and why the Taylor result is an approximation rather than an exact value.


## Part 2 — Dependence between input variables

Now assume the initial ice thickness and temperature deficit have a Pearson correlation coefficient $\rho=0.5$.

**2.1** State $\mathrm{Cov}(H_{\mathrm{ice},0},\Delta T)$ in terms of $\rho$, $\sigma_{H_0}$ and $\sigma_{\Delta T}$ and write the extra term in the **first-order output variance** compared with independent inputs. Is this term positive or negative? Justify using the derivatives from Part 1.

**2.2** Compare the Taylor standard deviations for $\rho=0$ and $\rho=0.5$. Explain physically why positive correlation has this effect on the propagated uncertainty. Does specifying the marginal distributions alone determine the output uncertainty?


## Part 3 — Lower-tail risk and Gaussian approximation 

**3.1** For the event $H_\mathrm{ice}<0.24\ \mathrm{m}$, compare the Monte Carlo and Gaussian non-exceedance probabilities from the reference values. State which estimate is higher and calculate their **absolute difference in percentage points**.

**3.2** Give two specific reasons why a Gaussian PDF with Taylor-propagated moments need not describe the simulated output distribution exactly, even if its mean and standard deviation are similar.

**3.3** Is agreement of the first two moments enough to validate a model for assessing exceptionally thin ice? Explain briefly.


## Part 4 — Monte Carlo accuracy and model limitations
**4.1** Compare the Monte Carlo and first-order Taylor standard deviations for independent inputs. Calculate their relative difference (using Monte Carlo as reference). Would increasing the number of Monte Carlo realizations $N$ necessarily eliminate this difference? Explain why or why not.

**4.2** Identify **one limitation of the input distributions** and **one limitation of the physical growth model**. For each, propose a practical improvement.



## How did things go? (Optional)

After the session, your group may share feedback with us (i.e. the teaching team) about the notebook and the written questions.

> By Lotfi Massarweh and Sandra Verhagen, Delft University of Technology. CC BY 4.0, more info [on the Credits page of Workbook](https://mude.citg.tudelft.nl/workbook-2026/credits.html).

```{custom_download_link} ./all_files_GA_1_6.zip
:text: ".zip assignment"
:replace_default: "True"
```
