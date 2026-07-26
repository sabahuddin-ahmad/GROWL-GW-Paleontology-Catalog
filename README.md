# GROWL - Gravitational Wave Paleontology Catalog

...

## Local Setup

### 0. Check Your Python Version

Run one or more of the following commands:

```bash
python --version
python3 --version
py --version
```

You can also check the version from inside Python:

```bash
python -c "import sys; print(sys.version)"
```

Use Python 3.10 or newer for this repository.

### 1. Clone the Repository

```bash
git clone <repository-url>
cd <repository-directory>
```

Replace `<repository-url>` and `<repository-directory>` with the actual repository details.

### 2. Create a Virtual Environment

#### macOS or Linux

```bash
python3 -m venv .venv
```

#### Windows

```powershell
py -m venv .venv
```

If `py` is unavailable, use:

```powershell
python -m venv .venv
```

### 3. Activate the Virtual Environment

#### macOS or Linux

```bash
source .venv/bin/activate
```

#### Windows PowerShell

```powershell
.\.venv\Scripts\Activate.ps1
```

#### Windows Command Prompt

```cmd
.venv\Scripts\activate.bat
```

After activation, the shell prompt should usually begin with `(.venv)`.

### 4. Upgrade pip

```bash
python -m pip install --upgrade pip
```

### 5. Install Dependencies

The main Python dependencies are listed in `requirements.txt`:

- `h5py`==3.16.0
- `numpy`==2.5.1
- `pandas`==3.0.3
- `matplotlib`==3.11.1

```bash
python -m pip install -r requirements.txt
```

### 6. Verify the Environment

Check the active Python interpreter and installed packages:

```bash
python --version
python -c "import sys; print(sys.executable)"
python -m pip list
```

Verify the project dependencies:

```bash
python -c "import h5py, numpy, pandas, matplotlib; print('Environment configured successfully.')"
```

### 7. Install Jupyter and the Kernel Package

Install Jupyter Notebook and `ipykernel` inside the active virtual environment:

```bash
python -m pip install jupyter ipykernel
```

### 8. Register the Virtual Environment as a Jupyter Kernel

While `.venv` is active, run:

```bash
python -m ipykernel install --user --name gw-astrophysics --display-name "Python 3.13 (GW Astrophysics)"
```

The arguments mean:

- `--name gw-astrophysics` sets the internal kernel identifier.
- `--display-name "Python 3.13 (GW Astrophysics)"` sets the name displayed in Jupyter and VS Code.

### 9. Start Jupyter Notebook

```bash
jupyter notebook
```

Open an `.ipynb` file and select:

```text
Kernel → Change Kernel → Python 3.13 (GW Astrophysics)
```

### 10. Start JupyterLab

```bash
jupyter lab
```

Select `Python 3.13 (GW Astrophysics)` from the kernel selector.

### 11. Select the Kernel in VS Code

1. Open the repository in VS Code.
2. Open an `.ipynb` notebook.
3. Click **Select Kernel** in the upper-right corner.
4. Choose **Jupyter Kernel** or **Python Environments**.
5. Select **Python 3.13 (GW Astrophysics)**.

You can also select the interpreter directly.

On macOS or Linux:

```text
.venv/bin/python
```

On Windows:

```text
.venv\Scripts\python.exe
```

### 12. Verify the Notebook Kernel

Run the following code in a notebook cell:

```python
import sys

print(sys.executable)
print(sys.version)
```

The executable path should point to the repository's `.venv` directory.

Verify the scientific packages:

```python
import h5py
import numpy as np
import pandas as pd
import matplotlib
import matplotlib.pyplot as plt
from matplotlib.lines import Line2D

print("Python:", sys.version)
print("h5py:", h5py.__version__)
print("NumPy:", np.__version__)
print("pandas:", pd.__version__)
print("Matplotlib:", matplotlib.__version__)
```

### 13. List Available Jupyter Kernels

```bash
jupyter kernelspec list
```

The output should include a kernel named `gw-astrophysics`.

### 14. Remove the Kernel

To remove the registered kernel later:

```bash
jupyter kernelspec uninstall gw-astrophysics
```

This removes the Jupyter kernel registration. It does not delete the `.venv` directory.

### 15. Deactivate the Virtual Environment

```bash
deactivate
```


### 16. Optional: Record Exact Dependency Versions

The supplied `requirements.txt` uses unpinned package names so that `pip` installs compatible current releases.

To record the exact versions installed in your local environment:

```bash
python -m pip freeze > requirements-lock.txt
```

Keep `requirements.txt` as the human-maintained dependency list and use `requirements-lock.txt` when exact reproducibility is required.