# Microsoft Sentinel SOC Lab
Windows security event collection using Azure Arc, Azure Monitor Agent and Data Collection Rules, with detections in Sentinel.

## Lab goals
- Onboard a Windows VM to Azure Arc
- Install Azure Monitor Agent extension
- Configure a Data Collection Rule for Security event logs
- Validate ingestion in Log Analytics and Sentinel
- Create an analytics rule for multiple failed logons
- Confirm incidents appear in Microsoft Defender

## Architecture
```mermaid
flowchart TB
  A[Windows 10 VM on VirtualBox] --> B[Windows Security Log\nEvent IDs 4624 4625 4688]
  A --> C[Azure Arc Connected Machine Agent]
  C --> D[Azure Arc Resource\nConnected Machine]

  D --> E[Azure Monitor Agent Extension\nAzureMonitorWindowsAgent]
  E --> F[Data Collection Rule\nSecurity Event Logs]
  F --> G[Azure Monitor Logs\nLog Analytics Workspace law soclab]

  G --> H[Microsoft Sentinel\nEnabled on workspace]
  H --> I[Analytics Rule\nMultiple Failed Logons]
  I --> J[Incidents and Alerts\nMicrosoft Defender Portal]
