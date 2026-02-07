---
title: Claude Desktop MCP Server to connect Azure
date: 2026-02-06 17:00:00 +1100
categories: [MCP, Claude]
tags: [mcp, claude, windows, azure]
---

## Pre-requisite :
- 1️⃣ Claude Desktop is installed in your Wndows 11
- 2️⃣ MCP server written in Python script.

## 🧠 High-Level Purpose

In short, the `mcpServers.json` file is the "brain center" of the setup. It is the configuration file that tells **Claude Desktop** exactly how to launch and connect to your **MCP Server**. In this project, the server is the Python script (`nc2_azure_mcp.py`) that Claude initiates via the command line instructions we provided.

![MCP Architecture](/assets/img/post20260206-mcp_architecture.png)
*Note: While many focus on RAG, MCP shifts the focus from data retrieval to active capability.*

---

### **Knowledge vs. Capability: Why MCP is Different**

When people discuss AI and data integration, the conversation usually revolves around **RAG (Retrieval-Augmented Generation)**. However, it is vital to understand that MCP serves a much more powerful purpose:

* **RAG is about Knowledge (The "Library Card")** RAG gives the AI access to a library of information. It can look up your old documents, PDFs, and historical data to "know" more facts. This is a **passive** flow of information where the AI learns from the past.

* **MCP is about Capability (The "Work Badge")** With the Azure MCP server I’ve built, Claude isn't just reading a static report about my environment; it is actually "logging in" to the system. It can check live status, list resources, and (with the right permissions) trigger actions. This is an **active** connection.

> **The Bottom Line:** While RAG tells the AI what happened in the past, **MCP allows the AI to see what is happening right now and do something about it.** In this Azure example, we are moving from simply "Chatting about my Cloud" to "Operating my Cloud" through a natural language interface.


## 🔍 Where to find mcpServers.json?
Go to Setting > Developer : Local MCP servers click "Edit Config". 

```json
{
  "mcpServers": [
    {
      "name": "NC2 Azure Prevalidation",
      "command": [
        "C:\\Users\\Andrew\\nc2-mcp\\venv\\Scripts\\python.exe",
        "C:\\Users\\Andrew\\nc2-mcp\\nc2_azure_mcp.py"
      ]
    }
  ]
}

```

## 🔄 Download MCP server python script 
- Source: https://github.com/andrewdatalab/andrew-ai-lab/blob/main/mcp/nc2_azure_mcp.py

## Azure authentication steps (Windows PowerShell)
☑ Step A — Install Azure CLI (if missing)

```powershell
winget install -e --id Microsoft.AzureCLI
```

☑ Step B — Login to Azure

```powershell
az login
```

- If your org needs device code login (common in locked-down environments):

```powershell
az login --use-device-code
```

☑ Step C — Set the correct subscription (very common issue)

- List subscriptions:

```powershell
az account list -o table
```

- Set one:

```powershell
az account set --subscription "<SUBSCRIPTION_ID_OR_NAME>"
```

- Confirm:

```powershell
az account show -o json
```

☑ Step D — Verify you can read the target RG

```powershell
az group show -n "<RESOURCE_GROUP_NAME>" -o json
```

⚠️ notes : If you get authorization errors, you need at least Reader access to that resource group.


## 🎯 End-to-end test (after everything is set)

Activate venv:

```powershell
cd $HOME\nc2-mcp
.\venv\Scripts\Activate.ps1
```

Confirm MCP dependency:

```powershell
python -c "import mcp; print('mcp ok')"
```

Confirm Azure auth:

```powershell
az account show -o json
```

🎯 Restart Claude Desktop and ask:

```
Use the NC2 Azure Prevalidation tool.
Resource group: <your-rg>
VNet name: <your-vnet>
Return PASS/FAIL with reasons.
```
