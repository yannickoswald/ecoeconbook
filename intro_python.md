(intro-python)=
# Introduction to Python and Programming

Welcome! This short chapter gets you writing and *running* Python code right away, then gently introduces core concepts—variables, data types, collections, control flow, and functions—using tiny examples from **ecological economics** (EE). By the end, you’ll build a simple **carbon-emissions calculator** and try a few practice exercises.

```{admonition} What you’ll learn
- How to run code cells in this book
- Python as a calculator (numbers, operators)
- Variables, basic data types, and printing
- Lists & dictionaries (for small datasets)
- `if` statements and `for` loops
- A tiny EE project: compute national CO₂ emissions and per-capita values
```

## How to use this book
- Press ▶️ (Run) on a code cell to execute it.
- Edit values, re-run, and observe how outputs change—*this is the learning loop*.
- Don’t worry about mistakes—errors are part of programming.

(section-hello)=
## Your first Python code

```{code-cell} python
# Hello, world — and you!
print("Hello, ecological economics!")
```

```{admonition} Try it
Change the message to include your name or city and run the cell again.
```

(basics-calculator)=
## Python as a calculator

```{code-cell} python
# Arithmetic
2 + 2, 10 - 3, 6 * 7, 22 / 7, 22 // 7, 22 % 7, 2 ** 10
```

- `/` = division (returns a float), `//` = floor division, `%` = remainder, `**` = exponent.

```{admonition} Quick check
What’s the difference between `22/7` and `22//7`? Why is one of them an integer?
```

(basics-variables)=
## Variables and basic data types

```{code-cell} python
country = "Austria"          # str (text)
population_million = 9.1     # float
year = 2023                  # int
is_oecd = True               # bool

type(country), type(population_million), type(year), type(is_oecd)
```

```{code-cell} python
# String formatting
print(f"{country} (OECD={is_oecd}) had a population of ~{population_million:.1f} million in {year}.")
```

(basics-collections)=
## Collections: lists and dictionaries

```{code-cell} python
# Small table of final energy use by fuel (illustrative numbers)
fuels = ["coal", "oil", "gas"]
energy_TJ = [120_000, 450_000, 380_000]   # Terajoules (TJ)
list(zip(fuels, energy_TJ))
```

```{code-cell} python
# A dictionary is great for named lookups
emission_factor_tCO2_per_TJ = {
    "coal": 94.6,   # illustrative values (for learning only)
    "oil": 73.3,
    "gas": 56.1
}
emission_factor_tCO2_per_TJ["coal"]
```

```{admonition} Note
The emission factors above are **illustrative for learning**. Real analyses require careful sourcing and documentation.
```

(control-flow)=
## Control flow: `if` and `for`

```{code-cell} python
x = 42
if x % 2 == 0:
    print("x is even")
else:
    print("x is odd")
```

```{code-cell} python
# Sum emissions across fuels
total_MtCO2 = 0.0
for fuel, energy in zip(fuels, energy_TJ):
    ef = emission_factor_tCO2_per_TJ[fuel]
    emissions = ef * energy / 1_000_000  # convert tCO2 to MtCO2
    print(f"{fuel:>4}: {emissions:.2f} MtCO2")
    total_MtCO2 += emissions

print(f"Total: {total_MtCO2:.2f} MtCO2")
```

(functions)=
## Functions: packaging reusable logic

```{code-cell} python
def compute_total_emissions_MtCO2(energy_by_fuel_TJ, ef_tCO2_per_TJ):
    """
    Compute total emissions in MtCO2 given:
      - energy_by_fuel_TJ: dict like {"coal": 120000, "oil": 450000, ...}
      - ef_tCO2_per_TJ: dict of emission factors
    """
    total = 0.0
    for fuel, tj in energy_by_fuel_TJ.items():
        total += (ef_tCO2_per_TJ[fuel] * tj) / 1_000_000
    return total

energy_TJ_dict = {"coal": 120_000, "oil": 450_000, "gas": 380_000}
compute_total_emissions_MtCO2(energy_TJ_dict, emission_factor_tCO2_per_TJ)
```

(project-emissions)=
## Mini-project: A tiny national CO₂ calculator

Let’s combine the pieces and compute **total** and **per-capita** emissions.

```{code-cell} python
country = "Austria"
population_million = 9.1
energy_TJ = {"coal": 120_000, "oil": 450_000, "gas": 380_000}

total_MtCO2 = compute_total_emissions_MtCO2(energy_TJ, emission_factor_tCO2_per_TJ)
per_capita_tCO2 = total_MtCO2 * 1_000_000 / (population_million * 1_000_000)

print(f"{country}: {total_MtCO2:.2f} MtCO2 total")
print(f"{country}: {per_capita_tCO2:.1f} tCO2 per person")
```

```{admonition} Explore
- Change `energy_TJ` values and see how totals respond.
- What happens to per-capita emissions if population changes?
- Add a new fuel (e.g., "biomass") with its own (illustrative) factor and re-run.
```

(exercises)=
## Practice exercises (very beginner-friendly)

1. **Per-capita emissions for multiple countries**

   Using the template below, compute total and per-capita emissions for each country and print a neat summary. (Use any illustrative numbers.)

   ```{code-cell} python
   countries = [
       {"name": "CountryA", "pop_million": 5.0,
        "energy_TJ": {"coal": 50_000, "oil": 200_000, "gas": 100_000}},
       {"name": "CountryB", "pop_million": 12.0,
        "energy_TJ": {"coal": 80_000, "oil": 300_000, "gas": 250_000}},
   ]

   for c in countries:
       total = compute_total_emissions_MtCO2(c["energy_TJ"], emission_factor_tCO2_per_TJ)
       percap = total * 1_000_000 / (c["pop_million"] * 1_000_000)
       print(f'{c["name"]}: {total:.2f} MtCO2 total, {percap:.1f} tCO2/person')
   ```

2. **Unit conversion: electricity emissions**

   Suppose a household uses **3,500 kWh** of grid electricity per year. If the grid emission factor is **0.25 tCO₂ per MWh**, compute annual household emissions.

   *Hints:* 1 MWh = 1,000 kWh.

   ```{code-cell} python
   kWh = 3_500
   ef_tCO2_per_MWh = 0.25
   MWh = kWh / 1_000
   household_tCO2 = MWh * ef_tCO2_per_MWh
   household_tCO2
   ```

3. **Add non-CO₂ gases (CO₂e)**

   Extend the calculator to include **CH₄** and **N₂O** using **illustrative** global warming potentials (e.g., CH₄: 28, N₂O: 265). Given small emissions in kt for each gas, compute **total CO₂e**.

   ```{code-cell} python
   # Illustrative values only
   ch4_kt = 150.0
   n2o_kt = 30.0
   GWP = {"CH4": 28, "N2O": 265}

   # Convert kt to t, multiply by GWP, convert back to Mt
   co2e_Mt = 0.0
   co2e_Mt += (ch4_kt * 1_000) * GWP["CH4"] / 1_000_000
   co2e_Mt += (n2o_kt * 1_000) * GWP["N2O"] / 1_000_000
   co2e_Mt
   ```

```{dropdown} Example solution for Exercise 1 (click to reveal)
```python
def summarize(countries, ef):
    rows = []
    for c in countries:
        total = compute_total_emissions_MtCO2(c["energy_TJ"], ef)
        percap = total * 1_000_000 / (c["pop_million"] * 1_000_000)
        rows.append((c["name"], total, percap))
    for name, total, percap in rows:
        print(f"{name:10s}  {total:6.2f} MtCO2   {percap:5.1f} tCO2/person")

summarize(countries, emission_factor_tCO2_per_TJ)
```
```

```{admonition} Key takeaways
- Programming is *experimentation*: edit → run → observe.
- Start small: numbers, variables, and simple collections take you far.
- Real EE work needs **good units** and **documented data sources**.
```

(next-steps)=
## What’s next?

In the next chapters we’ll deepen each idea:
- Variables and types — more on numbers, strings, and booleans  
- Working with lists and dicts — structuring small datasets  
- Functions and modules — writing reusable code  
- Basic plotting — visualizing data to reason about scale  

Here is a reference back to this intro: [](intro-python). Here is a reference to the code section above: [](section-hello).

---

```{admonition} Attribution & disclaimer
Emission factors and GWPs used here are **illustrative** for teaching. Replace with documented values for real analyses.
```
