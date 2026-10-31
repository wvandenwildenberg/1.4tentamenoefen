# Group assignment 1.6: Icy Dicey Propagation

An ice layer grows during a cold spell. How reliable is a prediction of its thickness after five days? You will use the Stefan ice-growth model to compare the uncertainty predicted by Taylor approximations with uncertainty obtained by Monte Carlo simulation.

You can preview this assignment in the [MUDE 2026 workbook](https://mude.citg.tudelft.nl/workbook-2026/assignments/GA1.6/README.html). The [version without solutions](https://mude.citg.tudelft.nl/workbook-2026/no_solutions/assignments/GA1.6/README.html) remains available. The workbook also provides a ZIP download of the assignment files.

**Friday group session:** during the first three hours, work through the [ice-growth notebook](./icey_dicey.ipynb) together and prepare handwritten reference notes. **At 11:30, close all laptops.** Your group will receive a separate set of questions to answer **by hand, without computers or other resources (including AI tools)**. You may consult the handwritten notes prepared during the first three hours. **Hand in your group's handwritten answers at 12:30.**

Before the session, read the [uncertainty propagation chapter](https://mude.citg.tudelft.nl/book/2026/propagation_uncertainty/overview.html), complete [Wednesday's workshop (Pipe Dreams)](https://mude.citg.tudelft.nl/workbook-2026/assignments/WS1.6/README.html) and the [programming assignment](https://mude.citg.tudelft.nl/workbook-2026/assignments/PA1.6/README.html).

You will practice second-order mean propagation, first-order variance propagation, sampling a non-linear model, interpreting CDFs and checking the influence of input correlation. The written questions assess your mathematical reasoning and interpretation of your results, not your ability to recall Python syntax.

**Files:** [icey_dicey.ipynb](./icey_dicey.ipynb) (preparation and numerical analysis) and `report.md` (the one-hour written questions, distributed when laptops close). The report is deliberately not included in the initial student download; teachers will provide it at 11:30.

> By Lotfi Massarweh and Sandra Verhagen, Delft University of Technology. CC BY 4.0, more info [on the Credits page of Workbook](https://mude.citg.tudelft.nl/workbook-2026/credits.html).

```{custom_download_link} ./all_files_GA_1_6.zip
:text: ".zip assignment"
:replace_default: "True"
```
