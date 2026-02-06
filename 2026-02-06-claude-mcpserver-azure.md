---
title: Cluade Desktop MCP Server to connect Azure
date: 2026-02-06 17:00:00 +1100
categories: [MCP, Claude]
tags: [mcp, claude, windows, azure]
---

Pre-requisite :
Claude Desktop is installed in your Wndows 11
MCP server written in Python script. In my case nc2_azure_mcp.py

In brief, in Claude Desktop, mcpServers.json is the configuration file that tells Claude Desktop how to start/connect to your MCP server. The server is your Python script (e.g., nc2_azure_mcp.py) that Claude launches via the command you configure.

Where to find mcpServers.json?
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

Azure authentication steps (Windows PowerShell)
Step A — Install Azure CLI (if missing)

```powershell
winget install -e --id Microsoft.AzureCLI
```

Step B — Login to Azure

```powershell
az login
```

If your org needs device code login (common in locked-down environments):

```powershell
az login --use-device-code
```

Step C — Set the correct subscription (very common issue)

List subscriptions:

```powershell
az account list -o table
```

Set one:

```powershell
az account set --subscription "<SUBSCRIPTION_ID_OR_NAME>"
```

Confirm:

```powershell
az account show -o json
```

Step D — Verify you can read the target RG

```powershell
az group show -n "<RESOURCE_GROUP_NAME>" -o json
```

If you get authorization errors, you need at least Reader access to that resource group.


5) End-to-end test (after everything is set)

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

Restart Claude Desktop and ask:

Use the NC2 Azure Prevalidation tool.
Resource group: <your-rg>
VNet name: <your-vnet>
Return PASS/FAIL with reasons.
