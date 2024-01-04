---
title: "Cyber Update 3rd Jan 2024"
date: 2023-01-04
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
     
*It seems so.



So, here's a couple of interesting articles and outcomes from today (4/1/24)

- Mandiant (Google) seem to have lost control of their Twitter/X - [Not ideal](https://www.bleepingcomputer.com/news/security/mandiants-account-on-x-hacked-to-push-cryptocurrency-scam/)

- CrowdStrike give an example of Defender scan logs being useful - [Brief article here](https://www.crowdstrike.com/blog/how-to-use-microsoft-protection-logging-for-forensic-investigations/)

    I will be providing an example in Splunk in the coming days on ingesting and triaging that data

- Excellent article by [Purple Team](https://ipurple.team/2024/01/03/scheduled-task-tampering/), which is a new resource to me personally. This article is on Scheduled Task Tampering by Chinese APT [HAFNIUM](https://malpedia.caad.fkie.fraunhofer.de/actor/hafnium) through registry modification
    
    I will be giving examples of how to collect this data in Splunk and will see how easy it is to simulate this activity in a future post

Thats it for now, duck broken, blog up!