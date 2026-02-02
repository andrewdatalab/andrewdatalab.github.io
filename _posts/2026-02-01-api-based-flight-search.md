---
title: API-based flight search or web scraping
date: 2026-02-02 17:00:00 +1100
categories: [AI, app]
tags: [llm, flight, ai-app]
---


## 📌 Introduction

This project is a **flight search and AI-assisted exploration tool** built using a combination of:

- **Public APIs**
- **Lightweight web data retrieval**
- **Local AI (LLM) models**
- **A simple web UI**

The goal is to demonstrate how **traditional APIs** and **modern AI workflows** can work together in a practical, real-world use case.

This blog focuses on:
- *Why* specific tools were chosen
- *How* the environment is set up
- *How* all components fit together

---

## ✈️ Why Use the Amadeus API?

Flight data is complex, dynamic, and regulated.  
Instead of relying entirely on web scraping, this project uses the **Amadeus Travel API** as its primary data source.

### What Is the Amadeus API?

The **Amadeus API** is a widely used travel industry platform that provides:

- Flight offers and pricing
- Airline and airport information
- Real-time availability data
- Structured and reliable responses

### Why API Over Pure Web Scraping?

| **API (Amadeus)** | **Web Scraping** |
|------------------|-----------------|
| Structured, reliable data | HTML structure can break |
| Official access & rate limits | Risk of blocking |
| Cleaner integration | Requires heavy parsing |
| Industry-grade accuracy | Data quality varies |


> In this project, **APIs are used as the primary source**, while AI is used to *interpret, filter, and enhance* the results.

---

## 🖥️ Environment Setup (Windows)

This project is developed and tested on **Windows** using Python.

### Prerequisites

Make sure the following are installed:

- **Python 3.10+**
- **Git**
- **VS Code** (recommended)

Verify Python installation:

```powershell
PS C:\> python --version
Python 3.11.x
```

## 🧪 Setting Up a Python Virtual Environment

A virtual environment isolates project dependencies and avoids conflicts.

1️⃣ Create a Virtual Environment

```powershell
PS C:\Projects\flight-ai> python -m venv venv
```

2️⃣ Activate the Virtual Environment

```powershell
PS C:\Projects\flight-ai> .\venv\Scripts\activate
```

You should now see:

```powershell
(venv) PS C:\Projects\flight-ai>
```

3️⃣ Install Dependencies

```powershell
pip install -r requirements.txt
```

## 📁 Project Folder Structure

Below is a simplified structure of the AI project:

```text
flight-ai/
├── app.py                 # Streamlit entry point
├── llm/
│   └── local_llm.py       # Local LLM (Ollama) integration
├── services/
│   ├── amadeus_client.py  # Amadeus API wrapper
│   └── search_logic.py    # Flight search logic
├── ui/
│   └── streamlit_ui.py    # UI components
├── .env                   # API keys and secrets
├── requirements.txt
└── README.md
```

## 🔐 Managing Secrets with .env

API keys must never be hard-coded.
This project uses a .env file to store sensitive values.

Example .env File

```env
AMADEUS_API_KEY=your_api_key_here
AMADEUS_API_SECRET=your_api_secret_here
```

> ⚠️ Make sure .env is added to .gitignore

## 📦 Loading Environment Variables in Python

To read values from .env, the project uses python-dotenv.

Install Dependency

```bash
pip install python-dotenv
```

Load .env in Python

```python
from dotenv import load_dotenv
import os

load_dotenv()

API_KEY = os.getenv("AMADEUS_API_KEY")
API_SECRET = os.getenv("AMADEUS_API_SECRET")

```

## 🤖 Local LLM Setup (Ollama)
Instead of calling cloud-based AI services, this project uses a local LLM.

Ollama Setup

```bash
ollama pull mistral
ollama serve
```

The model runs locally at:

```text
http://localhost:11434
```


## Streamlit UI
Streamlit is used to provide a simple web interface.

User inputs search criteria
Results are displayed interactively
AI responses are shown in real time

```bash
streamlit run app.py
```

## RESULT : 🧠 How Everything Fits Together (High Level)

```text
User Input (Streamlit)
        ↓
Flight Search (Amadeus API)
        ↓
Context Preparation
        ↓
Local LLM (Ollama)
        ↓
AI-Enhanced Output
```

## 📦 Source Code

The full source code for this project is available on GitHub:

👉 **andrew-ai-lab**  
https://github.com/andrewdatalab/andrew-ai-lab

Main script used in this post:
- `flight_search_app.py`

## 🏃 How to Run the Script

The main application in this repository is a Streamlit app.

1️⃣ Clone the Repository

```bash
git clone https://github.com/andrewdatalab/andrew-ai-lab.git
cd andrew-ai-lab
```

2️⃣ (Optional) Set Up a Virtual Environment

windows

```powershell
python -m venv venv
.\venv\Scripts\activate
```

mac

```bash
python -m venv venv
source venv/bin/activate
```

3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

4️⃣ Run the Streamlit App

```bash
streamlit run flight_search_app.py

```

## ✈️ flight search results

![RAG Flow](/assets/img/flight_search_ui.png)



