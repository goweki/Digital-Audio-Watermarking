# Environment Setup

This project uses a **Python virtual environment** to isolate dependencies and ensure a consistent development environment across all operating systems.

> **Recommended Python Version:** **3.12.x**  
> Verify your installation:
>
> ```bash
> python --version
> ```

---

## 1. Create the Virtual Environment

### Windows (PowerShell)

```powershell
py -3.12 -m venv .venv
```

If Python 3.12 is not installed:

```powershell
py install 3.12
```

### macOS

Using Homebrew:

```bash
brew install python@3.12
python3.12 -m venv .venv
```

### Linux (Ubuntu/Debian)

Install Python 3.12 and the virtual environment package:

```bash
sudo apt update
sudo apt install python3.12 python3.12-venv
python3.12 -m venv .venv
```

---

## 2. Activate the Virtual Environment

### Windows (PowerShell)

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks script execution:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

### Windows (Command Prompt)

```cmd
.venv\Scripts\activate.bat
```

### macOS / Linux

```bash
source .venv/bin/activate
```

After activation, your terminal should display:

```text
(.venv)
```

---

## 3. Upgrade pip

Upgrade `pip` and essential packaging tools before installing dependencies:

```bash
python -m pip install --upgrade pip setuptools wheel
```

---

## 4. Install Project Dependencies

Install all required packages:

```bash
pip install -r requirements.txt
```

Verify the active Python version:

```bash
python --version
```

Expected output:

```text
Python 3.12.x
```

---

## 5. Save Dependency Changes

Whenever you install, remove, or update packages, regenerate the dependency file:

```bash
pip freeze > requirements.txt
```

Commit the updated `requirements.txt` so everyone working on the project uses the same package versions.

---

## 6. Deactivate the Virtual Environment

When you're finished working on the project:

```bash
deactivate
```

---

## Project Structure

```text
project/
├── .venv/              # Virtual environment (not committed)
├── requirements.txt    # Project dependencies
├── README.md
└── ...
```

---

## Notes

- Use **Python 3.12.x** for maximum compatibility with the scientific Python ecosystem (`numpy`, `pandas`, `scikit-learn`, `librosa`, `numba`, `llvmlite`, etc.).
- Do **not** commit the `.venv/` directory to version control.
- Ensure `.venv/` is listed in your `.gitignore`.

Example `.gitignore`:

```gitignore
.venv/
__pycache__/
*.py[cod]
.ipynb_checkpoints/
```
