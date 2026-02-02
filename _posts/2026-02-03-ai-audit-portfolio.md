---
title: AI Audit Portfolio
date: 2026-02-03 10:00:00 +1100
categories: [AI, app]
tags: [audit, anomaly, financial, report, summary]
---

# windows environment set up

Owner: beyond_nam

# 🎯 Goal

Create a **private Python workspace (venv)** on **Windows 11** so you can run and test the audit scripts safely.

---

## 1️⃣ First check: Is Python installed?

Open **Command Prompt** or **PowerShell** and run:

```powershell
python--version
```

If you see something like:

```
Python3.11.x
```

✅ Good — continue.

If not:

- Download Python from **python.org**
- **IMPORTANT**: tick ✅ *“Add Python to PATH”* during install

---

## 2️⃣ Create a project folder

Choose a simple location, for example:

```powershell
mkdir ai-audit
cd ai-audit
```

This folder will hold:

- Python scripts
- Excel test data
- The virtual environment

---

## 3️⃣ Create the virtual environment (venv)

Run:

```powershell
python -m venv ai-audit
```

What this means in plain English:

> “Create a private Python environment called ai-audit inside this folder.”
> 

After this, your folder will look like:

```
ai-audit/
 ├ ai-audit/      ← theprivate Python room
 └ (empty)
```

---

## 4️⃣ Activate the venv (MOST IMPORTANT STEP)

### If using **PowerShell**:

```powershell
.\ai-audit\Scripts\Activate.ps1
```

### If using **Command Prompt (cmd)**:

```bash
ai-audit\Scripts\activate

```

After activation, you will see:

```
(ai-audit) C:\Users\YourName\ai-audit>

```

That `(ai-audit)` means:

> “You are now inside the private Python workspace.”
> 

---

## ⚠ If PowerShell blocks activation (common on Windows)

You may see:

> “running scripts is disabled”
> 

Fix it once:

```powershell
Set-ExecutionPolicy-Scope CurrentUser RemoteSigned

```

Then try activation again.

---

## 5️⃣ Install required Python packages (inside venv)

Now that venv is active, run:

```powershell
pip install pandas openpyxl scikit-learn reportlab openai

```

Everything installs **only inside this project**.

---

## 6️⃣ Add the Excel test file

Place `sample_gl.xlsx` into this folder:

```
ai-audit/
 ├ ai-audit/
 ├ sample_gl.xlsx
 ├ anomaly_detector.py
 ├ financial_summary.py
 └ report_generator.py

```

---

## 7️⃣ Run the scripts

```powershell
python anomaly_detector.py
python financial_summary.py
python report_generator.py

```

Expected results:

| Script | Output |
| --- | --- |
| anomaly_detector.py | `audit_flags.xlsx` |
| financial_summary.py | `monthly_summary.xlsx` |
| report_generator.py | `audit_report.pdf` |

---

## 🧠 Simple mental model for your son

| Computer | Real life |
| --- | --- |
| Windows | House |
| Project folder | Bedroom |
| venv | Locked drawer |
| pip install | Putting tools in that drawer |

---

## ✅ If he understands THIS

He already understands:

- How professionals isolate projects
- How real AI audit tools are built
- How to avoid breaking systems

That alone puts him **years ahead of typical students**.

If you want, next I can:

- Simplify error messages he may hit
- Convert this into a **1-page student checklist**
- Or add **AI explanation comments inside the scripts**

i need anomaly_detector.py

financial_summary.py

report_generator.py to download

Your three Python files are ready.

**Download them here:**

- anomaly_detector.py
- financial_summary.py
- report_generator.py

Put these files in the same folder as `sample_gl.xlsx`, activate your venv, and run:

```powershell
python anomaly_detector.py
python financial_summary.py
python report_generator.py

```

You should see:

- `audit_flags.xlsx`
- `monthly_summary.xlsx`
- `audit_report.pdf` generated automatically.
