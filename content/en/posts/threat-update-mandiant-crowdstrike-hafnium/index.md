---
title: "Cyber Interest - Jan 2024"
date: 2024-01-03
#toc: false
tags:
  - crowdstrike
  - mandiant
  - crypto
  - defender
  - mde
  - splunk
  - hafnium
  - sysmon
  - purpleteam
  - registry
  - scheduledtask
  - mitre
---

*Did this work?* 
     
*It seems so.*


So, here's a couple of interesting articles and outcomes from January 24, this page will be updated as the month progresses

### Microsoft Defender MP Scan Logs Used for DFIR (3rd Jan 2024)

CrowdStrike give an example of Defender scan logs being useful - [Brief here](https://www.crowdstrike.com/blog/how-to-use-microsoft-protection-logging-for-forensic-investigations/)  
*I will be providing an example in Splunk in the coming days on ingesting and triaging this telemetry*

### Scheduled Task Tampering by Chinese APT Hafnium (3rd Jan 2024)

Excellent article by [Purple Team](https://ipurple.team/2024/01/03/scheduled-task-tampering/), which is a new resource to me personally. This article is on Scheduled Task Tampering by Chinese APT [HAFNIUM](https://malpedia.caad.fkie.fraunhofer.de/actor/hafnium) through registry modification  
*I will be giving examples of how to collect this data from Sysmon with Splunk in a future post*

### Mandiant Twitter Hacked (3rd Jan 2024)

Mandiant (Google) seem to have lost control of their Twitter/X to apparent crypto scammers   - [Read more](https://www.bleepingcomputer.com/news/security/mandiants-account-on-x-hacked-to-push-cryptocurrency-scam/)
