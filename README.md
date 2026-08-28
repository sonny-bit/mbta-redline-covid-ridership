# Red Line Ridership Trends and the Impacts of COVID-19

An analysis of MBTA Red Line ridership from 2019 through 2025, examining how the COVID-19 pandemic reshaped commuter behavior and whether seasonal ridership patterns have reestablished themselves during the recovery.

**[Read the full analysis →](https://sonny-bit.github.io/mbta-redline-covid-ridership/)**

Built in R with the tidyverse, written in Quarto.

---

## Findings

**Weekday and weekend ridership recovered at very different rates.** All three day types lost roughly comparable shares of ridership during 2020-2021. Weekdays fell 65.1% against the 2019 baseline, Saturdays 53.8%, and Sundays 53.7%. Recovery is where they diverged sharply: weekend ridership has regained about 44% of what it lost, while weekday ridership has regained only 24.2%.

**That gap points to behavior, not service.** The MBTA has restored 92% of pre-pandemic service levels, so the trains are running. Weekend travel is leisure-driven and largely unaffected by remote work; weekday travel is not. The Red Line, which carries a large share of downtown office commuters, is the segment most exposed to that shift.

**Seasonality survived the disruption.** Ridership peaks in October and bottoms out in January, with a secondary dip in July, and the pattern repeats in every year from 2022 to 2025. The fall peak tracks the academic calendar rather than the weather, which is consistent with prior research on transit seasonality and unsurprising for a line serving MIT and Harvard.

The pre-COVID weekday baseline of roughly 250,000 average daily riders may no longer be a realistic target. The 2023-2025 weekday average sits near 127,000, about half that figure, though 2025 runs above every prior recovery year in nearly every month.

## Data

[MBTA Monthly Ridership by Mode and Line](https://mbta-massdot.opendata.arcgis.com/datasets/2048258a18354256a650d41f8fe4532c_0/explore), published by Massachusetts geoDOT through the MassDOT Open Data Portal and maintained by the MBTA's Office of Performance Management & Innovation.

4,864 rows covering July 2018 through May 2026, filtered here to Red Line observations for 2019 to 2025 (the years with complete twelve-month coverage). The snapshot in `data/` was retrieved on August 15, 2026 and is committed to the repository deliberately: the portal updates monthly, so a fresh download will not reproduce these figures exactly.

## What's in this repo

```
data/                    MBTA ridership CSV (retrieved RETRIEVAL-DATE)
index.html               Rendered analysis, served via GitHub Pages
redline-ridership.qmd    Quarto source (analysis code and prose)
redline-ridership.Rproj  RStudio project file
```

## Reproducing the analysis

Open `redline-ridership.Rproj` in RStudio rather than opening the `.qmd` directly. The project root is what `here()` resolves paths against, and the data load will fail without it.

```r
install.packages(c("tidyverse", "here", "scales", "plotly"))
```

Then render the `.qmd`. Output is written to `index.html` in the project root.

## Notes and limitations

The data is aggregated to the line level, so station-level questions are out of reach. Whether Wollaston recovered differently from Harvard cannot be answered here without joining to the MBTA's Gated Station Entries dataset. Ridership counts also say nothing about service quality, which matters for interpretation: the fall 2023 dip visible in the by-year chart coincides with a 16-day full closure of the Ashmont branch, and this dataset alone cannot separate a drop in demand from a drop in service availability.

Ridership figures count fare transactions rather than people, which likely undercounts riders who evade fares or enter through unstaffed gates. Since ridership data feeds MBTA service planning, that undercount has consequences worth naming, and the analysis includes a fuller discussion of the ethics involved.

## Background

Originally written as the final project for DACSS 601 (Data Analysis and Visualization with R) in the UMass Amherst DACSS MS program, and revised afterward. I ride the Red Line daily, which is how the project started.
