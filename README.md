## Topic

Comparison of world population growth models: Malthus and Cohen

## Team

* Weronika Przychodzeń 197505
* Zuzanna Warchoł 197829
* Giulia Bacchiocchi

## Problem Description

We study how the world population P(t) changed from 10000 BCE to 2023 and how it may continue to change. We are interested not only in the value of P in a given year, but above all in the **rate of change** dP/dt.
We compare two popular population growth models: Malthus and Cohen.

**Why differential equations for population models?**

* We know the mechanism of change (births and deaths), but not a ready formula for the population prediction in time P(t). A differential equation expresses this mechanism directly.
* The rate of change depends on the current state of the population (in easier words: the more people, the more births and deaths). An ordinary function of time cannot express this feedback.
* Once an initial condition is given, the solution determines the entire trajectory, and the asymptotic behavior can be read directly from the equation.
* Different assumptions about the right-hand side of the equation give different models, which can be compared within a single mathematical language.

**Assumptions common to both models:**

* P(t) is a continuous variable (the population is counted in millions of people),
* the world population is a closed system (no migration),
* the model is deterministic, with no age or regional structure.

## Research Question

**Main question:** Which population growth model (Malthus or Cohen) better describes the growth of the world population between 10000 BCE and 2023?

**Specific questions:**

1. Was historical population growth faster than exponential, i.e. is the Condorcet parameter c > 1 in Cohen's model?
2. After the turning point in the mid-1960s, did the nature of growth change (c < 1),which would mean an upper limit on the population?
3. How much do the forecasts of the two models for 2050 and 2100 differ?

## Models

### Malthus (1798)

Malthus observed that food resources grow in an arithmetic progression (a_n = a_0 + n·p), while the population grows in a geometric progression (b_n = b_0·q^n), so the population will sooner or later outstrip resources. He formulated the discrete version verbally, and  the differential equation is its modern version.

**Assumptions:** one species, identical individuals, constant birth and death rates, and unlimited resources (not realistic).

**Derivation:** every τ_r years an individual has n_r offspring, and every τ_s years a fraction n_s of the population dies. Then the birth rate is r_r = n_r/τ_r, the death rate is r_s = n_s/τ_s, and:

* equation: dP/dt = r·P, with r = r_r − r_s and P(t_0) = P_0
* solution: P(t) = P_0·e^{r(t − t_0)}
* doubling time (only for r > 0): T = ln 2 / r
* link to the discrete model: q = e^{rΔt}

*Remark:* r = (dP/dt)/P is the fraction of the population added per year, so its unit is 1/year.


| Condition | Behavior |
|---|---|
| r > 0 | exponential growth to infinity |
| r = 0 | constant population |
| r < 0 | extinction decay to 0 as time goes to infinity |

The per-capita growth rate (1/P)·dP/dt = r does not depend on P.


### Cohen (1995)

Cohen extends the logistic model: the carrying capacity K is not constant, but grows with the development of technology, agriculture and medicine, which is more realistic.

* dP/dt = r_C·P·(K − P)
* dK/dt = c·dP/dt
* initial conditions: P(t_0) = P_0, K(t_0) = K_0

The first equation says growth is proportional to P and to the free capacity K − P. The second says each additional person raises K by c people. c is the Condorcet parameter.

**Reduction to one equation.** From the second equation, K = K_0 + c(P − P_0). Put it into the first:

dP/dt = r_C·P·(a + (c − 1)·P), where a = K_0 − c·P_0.

So the per-capita rate is **(1/P)·dP/dt = r_C·(a + (c − 1)·P)**.
How it depends on P is decided by c:

**Cases:**

| c | Per-capita rate | Behavior |
|---|---|---|
| c = 0 | decreases | classical logistic model (Verhulst), P → K_0 |
| 0 < c < 1 | decreases | bounded growth (if a > 0), P_∞ = a/(1 − c) |
| c = 1 | constant | exponential growth with rate r_C·a, i.e. Malthus |
| c > 1 | increases | faster than exponential, blow-up in finite time |


### Comparison

| | Malthus | Cohen |
|---|---|---|
| Equation | dP/dt = rP | dP/dt = r_C·P·(K − P), dK/dt = c·dP/dt |
| Per-capita rate | constant: r | depends on c (decreases, constant or increases) |
| Environment | none | carrying capacity K, which itself grows |
| Parameters | r | r_C, c (and K_0) |
| Behavior as t → ∞ | P → ∞ (exponentially) | depends on c: limit, exponential growth or blow-up |
| Relationship | special case of Cohen (c = 1) | generalizes Malthus and Verhulst |

Verhulst (c = 0) and von Foerster (blow-up for c > 1) are treated as special cases or an extension, not as separate models.

### Variables, Parameters, Initial Conditions

| Symbol | Meaning | Model | Unit |
|---|---|---|---|
| t | time (years CE, 10000 BCE = −10000) | both | year |
| P(t) | world population size | both | million people |
| K(t) | carrying capacity | Cohen | million people |
| r | per-capita growth rate (births − deaths) | Malthus | 1/year |
| r_C | growth rate coefficient: per-person growth rate per million of free capacity | Cohen | 1/(million·year) |
| c | Condorcet parameter | Cohen | dimensionless |
| P_0 = P(t_0) | initial population (first year of data) | both | million people |
| K_0 = K(t_0) | initial carrying capacity | Cohen | million people |

r and r_C have different units, so they have different symbols.

* **r:** dP/dt is in million/year and P in million, so r = (dP/dt)/P is in 1/year.
* **r_C:** dP/dt is in million/year and P·(K − P) in million², so r_C = (million/year)/million² = 1/(million·year).


## Data
World population estimates from the S1 Appendix to Sojecka and Drozd-Rzoska (2025), PLoS ONE 20(5): e0323165. Data before 1950 are reconstructions with large uncertainty, which we take into account when interpreting the fit. Other sources (HYDE, U.S. Census Bureau, UN WPP, Our World in Data) are used for verification. The main source is the S1 Appendix.

## Roles of the Environments (to be verified during the project; add package versions)

* Wolfram Language [Wolfram Cloud]: description and formulation of the models, parameteres and variables, analytical solutions (`DSolve`), analysis of the special cases of Cohen's model (c = 0, 0 < c < 1, c = 1, c > 1), plots.
* MATLAB [version]: todo
* R [version, packages: ...]: todo

## Data Flow Structure (example – to be verified during the project)
todo 

## Running Instructions
todo

## Division of Work (proposal to be agreed upon)

* Person 1 (Weronika): dataset selection and literature review, simulations and estimation.
* Person 2 (Zuzanna): version control setup, models description, readme description, comparison description report and analysis.
* Person 3 (Giulia): data preparation (S1 Appendix → CSV), data quality control, forecasts plots and analysis.
* Jointly: research question, model comparison, conclusions, report and presentation.

## Tasks and Deadlines

* [x] Choice of team and topic (lab 4)
* [x] Mathematical model, formulation of the research problem (Mathematica) (lab 5)
* [x] Symbolic analysis and plots (Mathematica) (lab 6)
* [ ] MATLAB simulation (lab 10)
* [ ] Data analysis and report in R (lab 13)
* [ ] Presentation (labs 14 and 15)

## References

* Cohen J.E. (1995). Population growth and Earth’s human carrying capacity. Science, 269(5222), 341–346. https://doi.org/10.1126/science.7618100
* Kapitza S.P. (2010). On the theory of global population growth. Physics-Uspekhi, 53(12), 1287–1296. https://doi.org/10.3367/UFNe.0180.201012g.1337
* Lehman C., Loberg S., Wilson M., Gorham E. (2021). Ecology of the Anthropocene signals hope for consciously managing the planetary ecosystem. PNAS, 118(28), e2024150118. https://doi.org/10.1073/pnas.2024150118
* Malthus T.R. (1798). An Essay on the Principle of Population. London: J. Johnson.
* Sojecka A.A., Drozd-Rzoska A. (2024). Global population: from Super-Malthus behavior to Doomsday criticality. Scientific Reports, 14, 9853. https://doi.org/10.1038/s41598-024-60589-3
* Sojecka A.A., Drozd-Rzoska A. (2025). Verhulst-type equation and the universal pattern for global population growth. PLoS ONE, 20(5), e0323165. https://doi.org/10.1371/journal.pone.0323165
* von Foerster H., Mora P.M., Amiot L.W. (1960). Doomsday: Friday, 13 November, A.D. 2026. Science, 132(3436), 1291–1295. https://doi.org/10.1126/science.132.3436.1291
* Rudnicki R. Dynamika populacyjna [Population Dynamics]. https://im0.p.lodz.pl/~jbanasiak/MB/BiolPopRRudnicki.pdf
* Weisstein E.W. Malthusian Growth Model. Wolfram MathWorld.
