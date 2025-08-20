(intro-python)=
# Introduction to Python and Programming

Welcome!  
This short chapter gets you writing and *running* Python code right away, then gently introduces core concepts—variables, data types, collections, control flow, and functions—using tiny examples from **ecological economics** (EE).  

By the end, you’ll build a simple **carbon-emissions calculator** and try a few practice exercises.

:::{tip}
**What you’ll learn**
- How to install Python
- How to run code cells in this book  
- Python as a calculator (numbers, operators)  
- Variables, basic data types, and printing  
- Lists & dictionaries (for small datasets)  
- `if` statements and `for` loops  
- Functions
- A tiny EE project: compute national CO₂ emissions and per-capita values  
:::

---


(setup-python)=
# Getting Python set up (3 easy paths)

:::{admonition} TL;DR — pick one
- **No install**: Use **Google Colab** in the browser.
- **Beginner desktop**: Install **Anaconda** and use **Spyder** (MATLAB‑like).
- **Power users**: Install **Anaconda** and use **VS Code** (flexible, extensible).
:::

:::{tip}
No matter which route you choose, test your setup by running:

```python
print("Python is ready 🎉")
import sys, numpy as np
print(sys.version)
print("NumPy:", np.__version__)
```
:::

---

## Option A — Google Colab (browser, zero install)

:::{admonition} Why Colab?
- Runs in your browser; great for quick experiments or if you can’t install locally.
- Easy sharing via Google Drive.
:::

**Steps**
1. Go to <https://colab.research.google.com>.
2. Click **New Notebook** (top left).
3. In the first cell, paste the test code above and press **Shift+Enter**.

```{dropdown} Upload data or notebooks
- **Upload a local `.ipynb`**: File ▸ Upload notebook…
- **Mount Google Drive** to access files:
  ```python
  from google.colab import drive
  drive.mount('/content/drive')
  ```
```

```{dropdown} Install extra packages
Colab comes with many packages preinstalled. For others:
```python
!pip install plotnine openpyxl
```
```

:::{important}
Colab sessions are temporary. Save your work to **Drive** or **download** important files.
:::

---

## Option B — Anaconda + Spyder (beginner‑friendly)

:::{admonition} Why Spyder?
- Simple, MATLAB‑style interface: **editor + console + variable viewer**.
- Great for learning basics without lots of tooling.
:::

### 1) Install Anaconda
- Download **Anaconda Individual Edition** from <https://www.anaconda.com/download>.
- Install with defaults.

### 2) Create a clean environment (recommended)
```bash
# Windows (Anaconda Prompt) / macOS / Linux (Terminal)
conda create -n ecoecon python=3.11 -y
conda activate ecoecon
conda install numpy pandas matplotlib jupyterlab -y
```

```{dropdown} (Optional) Add more packages
```bash
conda install scipy seaborn xarray -y
# or with pip (inside the env):
pip install plotnine pyarrow
```
```

### 3) Launch Spyder
- Open **Anaconda Navigator** ▸ **Spyder** (choose env `ecoecon` if asked),  
  **or** from terminal:
  ```bash
  conda activate ecoecon
  spyder
  ```
- In the editor, open/create `hello.py`, paste the test code, press **Run** (▶).

```{dropdown} Ensure Spyder uses the right environment
In Spyder: **Preferences** ▸ **Python interpreter** ▸ **Use the following interpreter**  
Point it to your `ecoecon` env interpreter (Navigator usually handles this automatically).
```

---

## Option C — Anaconda + VS Code (flexible, not-so-beginner)

:::{admonition} Why VS Code?
- Excellent editor, **Python** and **Jupyter** extensions, debugging, terminals, Git.
- Works with both scripts (`.py`) and notebooks (`.ipynb`), and “cell” style `# %%`.
:::

### 1) Install prerequisites
- Install **Anaconda** (as above).
- Install **VS Code** from <https://code.visualstudio.com/>.
- In VS Code, install extensions:
  - **Python** (Microsoft)
  - **Jupyter** (Microsoft)

### 2) Create/select your conda environment
```bash
conda create -n ecoecon python=3.11 -y
conda activate ecoecon
conda install numpy pandas matplotlib jupyterlab -y
```

### 3) Tell VS Code which Python to use
- Open your project folder in VS Code.
- **Command Palette** (Ctrl/Cmd+Shift+P) ▸ **Python: Select Interpreter** ▸ choose the `ecoecon` env.
- Open a terminal in VS Code (**Terminal ▸ New Terminal**) — it should show `(ecoecon)`.

### 4) Run Python
- **Script**: create `hello.py`, run with the **▶ Run** button or right‑click ▸ **Run Python File**.
- **Notebook**: create a new **Jupyter Notebook** (`.ipynb`) and run cells.
- **Cell mode in .py**: use `# %%` to define cells, then click **Run Cell** above each cell.

```python
# %% first cell
print("Hello from a VS Code cell!")

# %% second cell
import numpy as np
np.arange(5)
```

```{dropdown} Debugging quick start
- Set a **breakpoint** (click the gutter).
- Press **F5** (Run and Debug) ▸ choose **Python File**.
- Inspect variables in the **Run and Debug** panel.
```

:::{note}
Common fix: If VS Code doesn’t “see” conda, set  
**Settings ▸ Python › Conda Path** to your `conda` executable, or launch VS Code from an **Anaconda Prompt**.
:::

---

## Choosing your path

- **Colab**: zero setup, great for quick labs and sharing; requires internet.
- **Spyder**: gentle desktop start; good for learning and small analyses.
- **VS Code**: most powerful and extensible; ideal as you scale up.

:::{admonition} Pro tip
Whichever path you pick, keep your work in **project folders** and use **environments** (`conda create -n …`) to avoid dependency conflicts.
:::



## How to use this book
- Press ▶️ (**Run**) on a code cell to execute it.  
- Edit values, re-run, and observe how outputs change — *this is the learning loop*.  
- Don’t worry about mistakes — **errors are part of programming**.  

---

(section-hello)=
## Your first Python code

```{code-cell} python
# %% This is a comment for you, the learner. It won’t affect execution.
# Classic "Hello world" — but with an EE twist
print("Hello, ecological economics!")
```

:::{admonition} Try it yourself
✏️ Change the message to include your name or city, then re-run the cell.
:::

---

(basics-calculator)=
## Python as a calculator

```{code-cell} python
# %% You can use Python just like a calculator:
2 + 2, 10 - 3, 6 * 7, 22 / 7, 22 // 7, 22 % 7, 2 ** 10
```

- `/` = division (returns a float)  
- `//` = floor division  
- `%` = remainder  
- `**` = exponent  

```{important}
Think: What’s the difference between `22/7` and `22//7`?  
Why is one of them an integer?
```

---

(basics-variables)=
## Variables and basic data types

```{code-cell} python
country = "Austria"          # str (text)
population_million = 9.1     # float
year = 2023                  # int
is_oecd = True               # bool

# %% Use type() to inspect the "kind" of a variable
type(country), type(population_million), type(year), type(is_oecd)
```

```{code-cell} python
# %% Example: formatted printing with f-strings
print(f"{country} (OECD={is_oecd}) had a population of ~{population_million:.1f} million in {year}.")
```

---

(basics-collections)=
## Collections: lists and dictionaries

```{code-cell} python
# %% Lists keep items in order
fuels = ["coal", "oil", "gas"]
energy_TJ = [120_000, 450_000, 380_000]   # Terajoules (TJ)

list(zip(fuels, energy_TJ))
```

```{code-cell} python
# %% Dictionaries are great for lookups
emission_factor_tCO2_per_TJ = {
    "coal": 94.6,   # illustrative values only!
    "oil": 73.3,
    "gas": 56.1
}

emission_factor_tCO2_per_TJ["coal"]
```

:::{warning}
⚠️ The emission factors above are **illustrative for learning**.  
Real analyses require careful sourcing and documentation.
:::

---

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
# %% Loop: sum emissions across fuels
total_MtCO2 = 0.0
for fuel, energy in zip(fuels, energy_TJ):
    ef = emission_factor_tCO2_per_TJ[fuel]
    emissions = ef * energy / 1_000_000  # tCO2 → MtCO2
    print(f"{fuel:>4}: {emissions:.2f} MtCO2")
    total_MtCO2 += emissions

print(f"Total: {total_MtCO2:.2f} MtCO2")
```

---

(functions)=
## Functions: packaging reusable logic

```{code-cell} python
def compute_total_emissions_MtCO2(energy_by_fuel_TJ, ef_tCO2_per_TJ):
    '''
    Compute total emissions in MtCO2 given:
      - energy_by_fuel_TJ: dict like {"coal": 120000, "oil": 450000, ...}
      - ef_tCO2_per_TJ: dict of emission factors
    '''
    total = 0.0
    for fuel, tj in energy_by_fuel_TJ.items():
        total += (ef_tCO2_per_TJ[fuel] * tj) / 1_000_000
    return total

energy_TJ_dict = {"coal": 120_000, "oil": 450_000, "gas": 380_000}
compute_total_emissions_MtCO2(energy_TJ_dict, emission_factor_tCO2_per_TJ)
```

---

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

:::{admonition} Explore
- Change `energy_TJ` values and see how totals respond.  
- What happens to per-capita emissions if population changes?  
- Add a new fuel (e.g., `"biomass"`) with its own factor and re-run.  
:::

---

(exercises)=
## Practice exercises (beginner-friendly)

1. **Per-capita emissions for multiple countries**  

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

```{dropdown} 💡 Example solution
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

2. **Unit conversion: electricity emissions**  

   ```{code-cell} python
   kWh = 3_500
   ef_tCO2_per_MWh = 0.25
   MWh = kWh / 1_000
   household_tCO2 = MWh * ef_tCO2_per_MWh
   household_tCO2
   ```

3. **Add non-CO₂ gases (CO₂e)**  

   ```{code-cell} python
   ch4_kt = 150.0
   n2o_kt = 30.0
   GWP = {"CH4": 28, "N2O": 265}

   co2e_Mt = 0.0
   co2e_Mt += (ch4_kt * 1_000) * GWP["CH4"] / 1_000_000
   co2e_Mt += (n2o_kt * 1_000) * GWP["N2O"] / 1_000_000
   co2e_Mt
   ```

---

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

Reference back to this intro: {ref}`intro-python`  
Reference to the first code section: {ref}`section-hello`

---

```{admonition} Attribution & disclaimer
Emission factors and GWPs used here are **illustrative**. Replace with documented values for real analyses.
```
