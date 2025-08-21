---
hide-toc: true
---

# Installing and running Python   <!-- Add this -->

## Getting Python set up (3 easy paths)

:::{tip}
**What you’ll learn**
- How to install and use Python
- How to run code cells in this book  
:::



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

### 1. Install Anaconda
- Download **Anaconda Individual Edition** from <https://www.anaconda.com/download>.
- Install with defaults.

### 2. Create a clean environment (recommended)
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

### 3. Launch Spyder
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
