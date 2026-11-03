# manuscript-advanced-drafts

**Dynamical Systems Model of Social Facilitation in Eating**

Working drafts of a research programme that models how company changes what and how much people eat, using differential equations. The programme builds from a single-diner intake model to coupled multi-agent systems.

## Background

People eat more in company than alone, an effect known as the **social facilitation of eating**. It has been documented since Bayer's 1929 chicken experiments, but it has mostly been studied observationally. This work gives it a mathematical form so that its mechanisms can be analysed, simulated and tested.

## Research arc

| Stage | Question | Approach | Code |
|---|---|---|---|
| 1. Single diner | How much do satiety, eating rate, meal duration and group size each matter for total intake? | Saturating intake model `E(t)` with a non-monotonic social-facilitation function `f(n)`. Sensitivity analysis and mixed partial derivatives. | [`social-facilitation`](https://github.com/newyorksnow/social-facilitation) |
| 2. Dyad | Do eating partners converge on each other's bite frequency, and what does the dynamics predict? | Two coupled ODEs with a shared affiliation motive. Closed-form gap solution, order preservation and reversal. Calibrated on the Food Intake Cycle dataset. | [`SMM`](https://github.com/newyorksnow/SMM) |
| 3. Design of coupling studies | Can coupling be estimated from data at all, and how many dyads are needed? | Errors-in-variables analysis of the per-dyad estimator, pooled estimator, closed-form power. | [`repoMM`](https://github.com/newyorksnow/repoMM) |
| 4. Group | How does facilitation evolve over a meal at a table of `k` people? | `k` coupled equations in which each diner's facilitation `F_i(t)` drifts towards a target set by how much their companions are still eating and how familiar they are. | In preparation |

## The modelling idea

Intake of diner `i` follows a saturating growth law that stops at their personal ceiling `Emax,i`. In the original model, the effect of other people was a single fixed number `f(n)`. The group extension replaces it with a time-varying, person-specific state:

- Each diner's facilitation `F_i(t)` moves gradually towards a target, which reproduces the lag observed in the early animal experiments.
- The target depends on `f(n)` and on how far each companion is from being full, weighted by how familiar the two diners are.
- Group size `n = k` is the number of equations in the system rather than a number plugged into a single-person formula.

## Findings so far

- In the single-diner model, satiety dominates intake. The social-facilitation term contributes comparatively little, and longer meals reduce rather than amplify its marginal effect.
- In the dyad model, a shared affiliation motive scales the speed of convergence but cannot by itself pull the diners together. Whether the initial leader keeps the lead depends on the asymmetry in their drives and decay rates.
- Fitted to solitary meals, the reduced models reach pooled R² of 0.85 and 0.79. The dyadic dynamics themselves still need data from eating pairs.
- Estimating coupling per dyad is infeasible with realistic meal lengths, so studies need pooled designs.

## Status

This repository is the home for the advanced manuscript drafts. The drafts will be added here as they stabilise; until then, the linked repositories hold the code behind each stage.

## Authors

Sophie Noemi Kieckens, with collaborators Mark D. Izgarshev and Emilia Giammaria.
