---
layout: post
current: post
cover: assets/images/cysa+/cysa_plus.jpg
navigation: True
title: CySA+ (CompTIA Cybersecurity Analyst) Full Glossary of Terms
date: 2023-03-01 10:30:00
tags: cysa+ comptia
class: post-template
subclass: 'post'
author: thomas
---

As I go through course material, study sessions, exploratory sessions, I will list all of the terms that have come up in a master alphabetized glossary list.

**Disclaimer**: These are notes I'm taking as I go through the material and I tend to summarize, paraphrase and add my own insights. Although I try to be as accurate as possible, there may be things I've misunderstood. Additionally, since I'm not writing a paper here, I may quote definitions I've found on various sites. I do want to mention that I used this [Udemy course](https://www.udemy.com/course/comptiacsaplus) for some of the definitions. If you see any mistakes and would like to fix them, please create a PR [here](https://github.com/thomashzhang/thomaszhang.com).

- **BIA** - Business Impact Analysis. Identifies organizational risk. Ex. could be something physical like an office/data center that could be at risk for power going out, or virtual like RTO, RPO stats.
- **Business Continuity Loss** - Can't fulfill contracts because of breakdown of infrastructure system. 
- **Compensating Control** - Secondary control that compensates the primary control. Ex. you may require a 16 digit password, but if the system doesn't allow for more than 12 digits, a compensating control could be to add 2FA. 
- **DLP** - Data Loss Prevention, to prevent data exfiltration.
- **Diamond Model of Intrusion Analysis** - Describes cyber attacks in the shape of a diamond with four parts: Adversary, Infrastructure, Capability, Target.
- **EDR** - Endpoint Detection and Response.
- **ERM** - Enterprise Risk Management.
- **IoC** - Indicators of Compromise.
- **MEF** - Mission Essential Function. Functions that can't be deferred on the business side.
- **MTD** - Maximum Tolerable Downtime. Max time a business can be down without irrevocable business failure.
- **RPO** - Recovery Point Objective. Longest time an organization can tolerate lost data being recoverable. Ex. a database goes down, and new data isn't recorded for 12 hours. That 12 hours is the RPO, and is that tolerable to the organization?
- **RSOI** - Return on Security Investment. By adding this security control, what's the expected return? This is a ratio.
- **RTO** - Recovery Time Objective. The time between systems going down to when it can be up again. Ex, if live databases all go down, how long does it take for them to recover?
- **Runbook** - Automated version of a playbook.
- **Sanitization** - Procedures that define how to dispose information or objects.
- **Scan-Patch-Scan** - A common motto for IT - scan for vulnerabilities, patch it, then scan it again to verify the patch.
- **SOAR** - Security Orchestration, Automation, Response, basically think of this as a "next-gen" SIEM.
- **Tabletop Exercises** - Simulated emergency situation on a table. But the downside is that the people don't go through the entire flow.
- **WRT** - Work Recovery Time. Fixing the secondary effects after RTO period. Ex. if live databases go down, and critical functions are working, how long does it take to ensure analytics are back up.