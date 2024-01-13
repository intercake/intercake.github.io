---
title: "Splunk Analysis - Hafnium GhostTask Scheduled Task Tampering"
date: 2024-01-05
tags:
  - splunk
  - hafnium
  - sysmon
  - purpleteam
  - registry
  - scheduledtask
  - mitre
  - T1053.005
  - T1053
---

### Objectives

- Deploy a suitable Sysmon configuration to record registry change telemetry
- Collect and analyse registry change telemetry
- Utilise tooling to ensure TTP data is suitable for Detection Engineering

### Summary

Excellent article by [Purple Team](https://ipurple.team/2024/01/03/scheduled-task-tampering/), which is a new resource to me personally. This article is on Scheduled Task Tampering by Chinese APT [HAFNIUM](https://malpedia.caad.fkie.fraunhofer.de/actor/hafnium) through registry modification
MITR

### Requirements

* Deploy Sysmon - [Test link - View my guide here](/intercake.github.io/content/en/posts/table-of-content/index.md)
* Create a suitable Sysmon collection policy
* Collect date with custom Splunk app
* Generate telemetry with Ghosttask
* Analyse registry logs and consider detection mechanics


### Resources

[Sysmon 15](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)  
[Splunk Universal Forwarder 9.1.2]("https://download.splunk.com/products/universalforwarder/releases/9.1.2/windows/splunkforwarder-9.1.2-b6b9c8185839-x64-release.msi")  
[Olaf Hartong Sysmon Modular](https://github.com/olafhartong/sysmon-modular)  
[Mitre ATT&CK Defense Evasion (TA003) Scheduled Task (T1053.005)](https://attack.mitre.org/techniques/T1053/005/)

### Installing Sysmon

Installing Sysmon requires the command below

```powershell
.\Sysmon64.exe -accepteula -i .\sysmonconfig-excludes-only.xml
```

To validate installation and configuration has occured correctly, -c provides a summary

```powershell
PS C:\Sysmon> .\Sysmon64.exe -c

System Monitor v15.11 - System activity monitor
By Mark Russinovich and Thomas Garnier
Copyright (C) 2014-2023 Microsoft Corporation
Using libxml2. libxml2 is Copyright (C) 1998-2012 Daniel Veillard. All Rights Reserved.
Sysinternals - www.sysinternals.com

Current configuration:
 - Service name:                  Sysmon64
 - Driver name:                   SysmonDrv
 - Config file:                   .\sysmonconfig-excludes-only.xml
 - Config hash:                   SHA256=BF5B3A2959FBAF8FE7E10D943BC89F5F5C7E00AC9174DAA92001C1D49EEA0753

 - HashingAlgorithms:             SHA1,MD5,SHA256,IMPHASH
 - Network connection:            enabled
 - Archive Directory:             \Sysmon\
 - Image loading:                 enabled
 - CRL checking:                  disabled
 - DNS lookup:                    disabled
```

```sysmon
[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = false
renderXml = 1
source = XmlWinEventLog:Microsoft-Windows-Sysmon/Operational
index=hafnium_ghosttask
```

```serverclass
[serverClass:splunk-content-hafnium-ghosttask:app:splunk_ingest_actions]
restartSplunkWeb = 0
restartSplunkd = 0
stateOnClient = enabled

[serverClass:splunk-content-hafnium-ghosttask:app:Splunk_TA_microsoft_sysmon]
restartSplunkWeb = 0
restartSplunkd = 0
stateOnClient = enabled
```