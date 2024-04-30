# Azure Cloud Detection Lab

This repository contains instructions and resources for setting up an Azure Cloud Detection Lab. The lab focuses on configuring and deploying Azure resources such as Log Analytics Workspace, Virtual Machines, and Azure Sentinel, implementing network and virtual machine security best practices, utilizing data connectors to bring data into Sentinel for analysis, understanding Windows Security Event logs, configuring Windows Security Policies, and utilizing KQL to query logs.

## Contents

1. [Creating a Resource Group](#creating-a-resource-group)
2. [Creating Virtual Machine](#creating-virtual-machine)
3. [Enabling Just In Time VM Access using Microsoft Defender](#enabling-just-in-time-vm-access-using-microsoft-defender)
4. [Creating Log Analytics Workspace](#creating-log-analytics-workspace)
5. [Microsoft Sentinel](#microsoft-sentinel)
6. [Microsoft Sentinel Data Connectors](#microsoft-sentinel-data-connectors)
7. [Connecting to Your Windows 10 Virtual Machine via RDP](#connecting-to-your-windows-10-virtual-machine-via-rdp)
8. [Kusto Query Language (KQL)](#kusto-query-language-kql)

## Goals

● Configure and deploy various Azure resources such as Virtual Machines, Log Analytics and Microsoft Sentinel.
● Implement best security practices for network and virtual machine configuration.
● Implement and utilize data connectors to feed data into Microsoft Sentinel for analysis.
● Understand and configure Windows Event logs and Windows Security Policies.
● Implement and utilize KQL (Kusto Query Language) to query for filter out logs

## Instructions

### Creating a Resource Group

1. Log in to your Azure portal.
2. Click on "+Create" to create a resource group.
3. Name your resource group.
4. Click on "Review and Create" to create your resource group.

### Creating Virtual Machine

1. Go back to your home page in the Azure portal.
2. Click on "Create" to create a virtual machine.
3. Fill in the required details.
4. Create a username and password.
5. Click on "Review and Create".
6. Click on "Create".

### Enabling Just In Time VM Access using Microsoft Defender

1. Navigate to Microsoft Defender for Cloud service offered by Azure.
2. Select your subscription.
3. Click on "Enable all plans".
4. Go into the inventory section.
5. Click on the server created earlier.
6. Select the recommendation "Management Ports of Virtual Machine should be protected with just-in-time network access control".
7. Click on the "Fix" button.

### Creating Log Analytics Workspace

1. Search for Log Analytics Workspaces.
2. Select "Create Log Analytics Workspace".
3. Name the workspace and select the resource group.
4. Click on "Review + Create".

### Microsoft Sentinel

1. Search for Microsoft Sentinel from the Home Screen.
2. Select "Create Microsoft Sentinel".
3. Select the Log Analytics Workspace created earlier.
4. Click on "Add".

### Microsoft Sentinel Data Connectors

1. Select Data Connectors from the Microsoft Sentinel screen.
2. Select "More Data Connectors".
3. Search and select "Windows Security Events".
4. Click on "Install".
5. Click on "Open Connector Page".
6. Click on "+Create data collection rule" and name the rule.

### Connecting to Your Windows 10 Virtual Machine via RDP

1. Identify the IP Address of your Virtual Machine.
2. Search for "Remote Desktop Connection" in the start menu.
3. Enter the credentials.
4. Access the Windows 10 desktop of the virtual machine.
5. Search for Event Viewer > Windows Log > Security Logs.
6. Use the Find option to Find the Event ID 4624.

### Kusto Query Language (KQL)

1. Go back to Microsoft Sentinel > Logs.
2. Type the following command into the query box: `SecurityEvent | where EventID == 4624`.
3. Click on the "Run" button.
4. To filter the results, add the project command to the query, e.g., `SecurityEvent | where EventID == 4624 | project TimeGenerated, Computer, Account`.
