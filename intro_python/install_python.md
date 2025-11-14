(basics-install)=


# Installing and running Python   <!-- Add this -->


## A note on learning to code/programming

Coding is omnipresent in today's world. Computer code runs your phones, laptops and every AI you ever interact with.
But coding is even more than that. Coding is a tool to find efficient solutions to problems and to build 'artificial' models of the world around us that can be explored. Learning to code is an excellent pathway to shape your own thinking: It combines logic and creativity like few other activities. 

Therefore please note the following.

At all times in this ebook and course that you follow - try to really understand things that you learn and do everything yourself. Do not use Generative AI to come up with coding solutions for you during exercises, as then the entire course will be a complete waste of your time. For your future success and capability it is absolutely essential that you build your own thinking and scienitific abilities, as if Generative AI and even the Internet would not exist. 

Only if you approach it this way, you will later on benefit from the synergies you can generate with these advanced technologies. 

## Getting Python set up (3 easy paths)

:::{admonition} What you’ll learn
- How to install and use Python
- How to run code cells in this book  
:::



:::{admonition} TL;DR — pick one
- **OPTION A No install**: Use **Google Colab** in the browser. But requires google account.
- **OPTION B Beginner desktop**: Install **Anaconda** and use **Spyder** as an integrated development environment (IDE).
- **OPTION C Power users**: Install **Anaconda** and use **VS Code** (flexible, extensible).
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

 Why Colab?
- Runs in your browser; great for quick experiments or if you can’t install locally.
- Easy sharing via Google Drive.


Steps
1. Go to <https://colab.research.google.com>.
2. Click **New Notebook** (top left).
3. In the first cell, paste the test code above and press **Shift+Enter**.



Install extra packages
Colab comes with many packages preinstalled. For others post the following in a code cell.

```python
python !pip install yourpackage
```



IMPORTANT! Colab sessions are temporary. Save your work to **Drive** or **download** important files.


```{dropdown} Upload data or notebooks
- **Upload a local `.ipynb`**: File ▸ Upload notebook…
```

---

## Option B — Anaconda + Spyder (beginner‑friendly)

 Why Spyder?
- Simple, MATLAB‑style interface: **editor + console + variable viewer**.
- Great for learning basics without lots of tooling.


1. Install Anaconda
- Download **Anaconda Individual Edition** from <https://www.anaconda.com/download>.
- Install with defaults.

2. Create a clean environment (recommended)
```bash
# Windows (Anaconda Prompt) / macOS / Linux (Terminal)
conda create -n ecoecon python=3.11 -y
conda activate ecoecon
conda install numpy pandas matplotlib jupyterlab -y
```


Launch Spyder

- Open **Anaconda Navigator** ▸ **Spyder** (choose env `ecoecon` if asked),  
  **or** from terminal:
  ```bash
  conda activate ecoecon
  spyder
  ```
- In the editor, open/create `hello.py`, paste the test code, press **Run** (▶).

---

## Option C — Anaconda + VS Code (flexible, not-so-beginner)


 Why VS Code?
- Excellent editor, **Python** and **Jupyter** extensions, debugging, terminals, Git.
- Works with both scripts (`.py`) and notebooks (`.ipynb`), and “cell” style `# %%`.


1) Install prerequisites
- Install **Anaconda** (as above).
- Install **VS Code** from <https://code.visualstudio.com/>.
- In VS Code, install extensions:
  - **Python** (Microsoft)
  - **Jupyter** (Microsoft)

2) Create/select your conda environment
```bash
conda create -n ecoecon python=3.11 -y
conda activate ecoecon
conda install numpy pandas matplotlib jupyterlab -y
```

3) Tell VS Code which Python to use
- Open your project folder in VS Code.
- **Command Palette** (Ctrl/Cmd+Shift+P) ▸ **Python: Select Interpreter** ▸ choose the `ecoecon` env.
- Open a terminal in VS Code (**Terminal ▸ New Terminal**) — it should show `(ecoecon)`.

4) Run Python
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

:::{tip}
**For detailed tutorials to install Python and get started with programming**
- You can also have a look at Prof. Tom Beucler’s ebooks (who teaches environmental machine learning at UNIL).  
- However, we will dive into everything we need in the next chapter, too.  
- Here is [Tom’s intro to running Python scripts](https://tbeucler.github.io/2024_MLEES_Ebook/Milton/00_Running_Python_Scripts.html)  
- Here is [an introduction to Python by Tom](https://tbeucler.github.io/2024_MLEES_Ebook/IP/intro_python.html)  
:::

:::{admonition} Pro tip
Whichever path you pick, keep your work in **project folders** and use **environments** (`conda create -n …`) to avoid dependency conflicts.
:::
