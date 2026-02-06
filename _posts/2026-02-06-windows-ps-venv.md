---
title: "How to set venv on Windows 11 PS"
date: 2026-02-06
categories: [Basics, Windows]
tags: [venv, windows]
---

Step 1: Create Project Directory

```
cd $HOME
mkdir nc2-mcp
cd nc2-mcp
```

Step 2: Create Virtual Environment
```
python -m venv venv
```

Step 3: Activate the Virtual Environment

```
.\venv\Scripts\Activate.ps1
```

Successful activation looks like:

```
(venv) PS C:\Users\Andrew\nc2-mcp>
```

Step 4: Upgrade pip

```
python -m pip install --upgrade pip
```

Step 5: Install MCP Package

```
pip install mcp
```

Step 6: Deactivate Virtual Environment (Optional)

```
deactivate
```

