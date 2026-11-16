# Cinema Integration Planner

A small personal learning project for practising Vercel deployment and capacity planning. Non-commercial. One `index.html`, no dependencies, no backend, no API keys, no database.

Enter how many cinemas you need to integrate, the hours each one takes, and how much time you have. The page shows whether the plan fits.

## Run it

Open `index.html` in a browser. To deploy, import the repository in Vercel as a static site (framework preset: Other, no build command, no output directory).

## Inputs

| Input | Symbol | Rule |
| --- | --- | --- |
| Number of cinemas | `N` | whole number, 1 to 500 |
| Research, development, QA hours per cinema | `R`, `D`, `Q` | 0 to 500 each, sum above 0 |
| Available working hours per week | `H` | 0.5 to 168 |
| Target delivery timeline in weeks | `W` | whole number, 1 to 520 |

Invalid input shows an inline message and hides the results.

## Formulas

```
Hours per cinema      = R + D + Q
Total required effort = N × (R + D + Q)
Available capacity    = H × W
Capacity utilisation  = Total effort ÷ Available capacity × 100
Capacity gap          = Available capacity − Total effort
Estimated completion  = Total effort ÷ H            (weeks)
```

A positive gap is spare hours, a negative gap is a shortfall. Status colours: utilisation up to 85% is comfortable, above 85% up to 100% is tight, above 100% is over capacity. Estimated completion compares directly with the target `W`.

## Scenario presets

Presets fill the hours, weekly capacity and timeline. The number of cinemas is left as you set it.

| Preset | Research | Dev | QA | Hours/week | Weeks |
| --- | --- | --- | --- | --- | --- |
| Optimistic | 2 | 6 | 2 | 16 | 12 |
| Base | 4 | 10 | 3 | 12 | 12 |
| Pessimistic | 8 | 18 | 6 | 8 | 12 |

Example, base preset with 10 cinemas: effort = 10 × 17 = 170 h, capacity = 12 × 12 = 144 h, utilisation = 118.1%, gap = −26 h, completion = 14.2 weeks.
