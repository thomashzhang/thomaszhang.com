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

- **ABAC** - Attribute-Based Access Control. Each subject possess a list of attributes for what they can access. Most complex type of access control to implement, but most flexible.
- **ACL** - Access Control List. The permissions for some resource.
- **Active Scanning** - Vulnerability scanning that can consume resources (actively probes targets).
- **Aircrack ng** - Bunch of wireless tools. Aircrack ng specifically allows you to "crack" WEP passwords.
- **AUP** - Acceptable Use Policy. Policy that governs how employees can use company equipment and internet.
- **ALE** - Annual Loss Expectancy. The expected cost to an organization for an event. Ex. if there's a 5% chance a laptop will need replacing, and it's $2,000k, then the ALE of that event (losing a laptop) is $100.
- **BAS** - Building Automation System. Configuration and monitoring for the building. These can turn on/off the AC, or lights, heat, etc.
- **BIA** - Business Impact Analysis. Identifies organizational risk. Ex. could be something physical like an office/data center that could be at risk for power going out, or virtual like RTO, RPO stats.
- **Blue Team** - The defense side of security like the IT admins or cybersecurity analysts. Contrast this with the red team.
- **Business Continuity Loss** - Can't fulfill contracts because of breakdown of infrastructure system. 
- **CAB** - Change Advisory Board. Group of leaders in an org that have the technical know-how to approve a change.
- **CAN** - (CAN bus) Controller Area Network. Don't confuse this with Campus Area Network.
- **CAPEC** - Common Attack Pattern and Enumeration Classification. Knowledge base by MITRE that focuses on application security.
- **CASB** - Cloud Access Security Broker - A Cloud Access Security Broker, or CASB, is cloud-hosted software or on-premises software or hardware that act as an intermediary between users and cloud service providers. See [this](https://www.skyhighsecurity.com/en-us/cybersecurity-defined/what-is-a-casb.html) for more details.
- **CCE** - Common Configuration Enumeration. Scheme for secure configuration checks across multiple sources. Basically these are best practice statements.
- **Compliance Scan** - Scan that just goes through a checklist. Think PCI DSS scanning.
- **CDM** - Continuous Diagnostics and Mitigation - Helps US government agencies identify cybersecurity risks.
- **CIS** - Center for Internet Security. Non profit that publishes wellknown "Top 20 Critical Security Controls." This org feels like a broader OWASP. 
- **Compensating Control** - Secondary control that compensates the primary control. Ex. you may require a 16 digit password, but if the system doesn't allow for more than 12 digits, a compensating control could be to add 2FA.
- **COSO** - Committee of Sponsoring Organizations of the Treadway Commission. Provides guidance on governance-related topics like fraud, controls, finance, and ethics. These are best practices (not a regulation or law).
- **Core Impact** - Penetration testing tool.
- **CPE** - Common Platform Enumeration - scheme that nmap, or any other tool, can use to fingerprint/identify hardware devices, OS version, applications, etc. This is developed by MITRE.
- **CVE** - Common Vulnerabilities and Exposures. Scheme for identifying vulnerabilities. This was developed by MITRE and adopted by NIST. CVE-YYYY-### (this is how CVEs are identified, YYYY is the year).
- **CVSS** - Common Vulnerability Scoring System. This is a more objective measure at deciding how critical a vulnerability is. Scored on 0-10. Uses exploit and impact with temporal and environmental factors to determine this score. You can use [this](https://www.first.org/cvss/calculator/3.1) to create your CVSS score.
- **DAC** - Discretionary Access Control. Each resource is protected by an ACL and managed by the resource owners. Think Windows Server, DAC is used there.
- **Discovery Scan** - A scan that just inventories what's out there, think nmap. Fast, but not in depth.
- **DLP** - Data Loss Prevention, to prevent data exfiltration.
- **Diamond Model of Intrusion Analysis** - Describes cyber attacks in the shape of a diamond with four parts: Adversary, Infrastructure, Capability, Target.
- **DKIM** - Domain Keys Identified Mail - similar functionality as SFP, but much more secure (and less cumbersome) by instead of using IP addresses for verification, it'll use a public key record to verify an email (that's been signed) is legitimate. Read more [here](https://www.courier.com/guides/dmarc-vs-spf-vs-dkim/).
- **DMARC** - Domain-based Message Authentication, Reporting & Conformance. This is a very powerful email authentication protocol that uses both SPF and DKIM to decide the authenticity of an email. Read more [here](https://www.courier.com/guides/dmarc-vs-spf-vs-dkim/). Also note how this differs from just SFP (validates email sender IP) and DKIM (validates email sender's cryptographic signature).
- **EDR** - Endpoint Detection and Response.
- **eFuse** - Essentially a software fuse. Generally this refers to the state of firmware on your computer. If an eFuse is triggered (by tampering or whatnot), the firmware can no longer be trusted.
- **EMM** - Enterprise Mobility Management. Essentially an MDM solution with even broader capabilities. Many use the terms interchangeably.
- **ERM** - Enterprise Risk Management.
- **ESA** - Enterprise Service Architecture. A framework for defining baselines, goals and methods used to secure a business.
- **Fast Assessment Scan** - Fast version of a vulnerability scan (versions of hosts, minor vulnerabilities/ configuration issues).
- **Fieldbus** - Used in OT networks to link PLCs.
- **Fingerprinting** - Mapping out the layout of a device (open ports, OS version etc.). Contrast this to footprinting.
- **FISMA** - Federal Information Security Management Act. Requirements for federal organizations to adopt information assurance controls.
- **Footprinting** - Mapping out the layout of the network. We're not focused on the details of a single device. Contrast this to fingerprinting.
- **FPGA** - Field Programmable Gate Array. A processor that can be programmed for a function that a customer wants, rather than being set by the manufacturer.
- **Full Assessment Scan** - Fully scans every single host. It's a lot more intrusive.
- **Full Disclosure Mailing List** - A public, vendor-neutral forum for detailed discussion of vulnerabilities and exploitation techniques, as well as tools, papers, news, and events of interest to the community. The relaxed atmosphere of this quirky list provides some comic relief and certain industry gossip. More importantly, fresh vulnerabilities sometimes hit this list many hours or days before they pass through the Bugtraq moderation queue. See the website [here](https://seclists.org/fulldisclosure/).
- **GLBA** - Gramm-Leach-Bliley Act. Requirements that define an individual's financial information held at financial institutions and others.
- **Hack Back** - Using offensive techniques to attack an attacker (potentially when they are in a honeypot). This is usually not allowed at most organizations. There are legal repercussions potentially.
- **Hardening** - Reduce attack service. Remove or disable anything that's unneeded, use least privilege. Always update the system, patch it. Uninstall unnecessary network protocols, enforce ACL, etc.
- **Hashcat** - Password cracking tool (for passive cracking) of hashes. Installed by default on Kali Linux. Similar to John the Ripper.
- **HMI** - Human Machine Interface. Ex a button, knobs, keystrokes, screens.
- **Honeypot** - A host or server that's setup to lure an attacker to it. Ex. it might have x amount of bitcoin, or it has fake passwords, it will allow a security analyst to look at the attacker's behavior.
- **hPing** - Open source packet generator. Allows the user to craft packets.
- **HSM** - Hardware Security Module. Appliance that is used to generate and store keys that is less susceptible to tampering than software solutions.
- **ICS** - Industrial Control System. Network that manages embedded devices.
- **IoC** - Indicators of Compromise.
- **John the Ripper** - Password cracking tool (reversing hashes), not diving too deep, see Hashcat for a rough definition.
- **Jumpbox** - The one box that has the permissions to go through firewall and touch the DMZ from the internal network. This is a single point of access.
- **MAC** - Not MAC address, but Mandatory Access Control. Resources are protected by inflexible rules. Think about labels. Secret/top secret, etc. SELinux implements MAC. Most other systems don't use this.
- **Maltego** - Maltego is software used for open-source intelligence and forensics, developed by Paterva from Pretoria, South Africa. Maltego focuses on providing a library of transforms for discovery of data from open sources, and visualizing that information in a graph format, suitable for link analysis and data mining. This is taken from [Wikipedia](https://en.wikipedia.org/wiki/Maltego).
- **Maturity Model** - Part of ESA framework for how mature the frameworks are. There's a common one that's 5 levels with level 1 being very reactive in terms of security.
- **MEF** - Mission Essential Function. Functions that can't be deferred on the business side.
- **Metasploit** - Allows a user to use known exploits to see if a server is vulnerable to that specific exploit.
- **MFA** - Multifactor Authentication. Use a separate factor to authenticate (something you are, something you know, something you have, somewhere you are, etc.). Two passwords does not count as MFA. But a password + OTP counts.
- **MITRE ATT&CK** - Essentially a database of all known attacks through all stages of the attack. This includes how to detect and stop these attacks.
- **Modbus** - A communication protocol used in operational technology networks. Contrast this to TCP/IP - Modbus is a different way of thinking.
- **MOU** - Memorandum of Understanding -  Preliminary or exploratory agreement for parties to work together. This is not legally binding and doesn't involve monetary exchange.
- **MTBF** - Mean Time Between Failures. How long do we expect a system to last? Ex. hard drives might only be expected to last 10 years before failing.
- **MTD** - Maximum Tolerable Downtime. Max time a business can be down without irrevocable business failure.
- **NASL** - Nessus Attack Scripting Language. Used for creating Nessus plugins.
- **Nessus** - Free remote vulnerability scanner.
- **NIST 4 Steps of Incident Response** - 1. Preparation. 2. Detection and Analysis. 3. Containment, Eradication and Recovery. 4. Post-Incident Activity.
- **NIST Cybersecurity Framework** - A risk-informed model of ESA (Identify, Protect, Detect, Respond, and Recover).
- **NMAP** - Network scan (see footprinting). A very common tool to be familiar with. See more information [here](https://www.upguard.com/blog/how-to-use-nmap). There are also lots of tools out there that will provide a visual interface for NMAP like Zenmap.
- **NSE** - Nmap Scripting Engine - Lua based scripting engine for Nmap to carry out detailed probes.
- **NVD** - National Vulnerability Database. Superset of CVE that includes more information (like remediation instructions).
- **OpenVAS** - Open source vulnerability scanner that split off the Nessus codebase when Nessus became a commercial software.
- **OT** - Operational Technology. Think manufacturing plants. These prioritize availability and integrity, less so on confidentiality.
- **PACS** - Physical Access Control System. Components that facilitate the centralized monitoring of security mechanisms within offices and data centers.
- **PAN** - Not personal access network (unless it's used in that context) but stands for Privileged Access Management (solution). This is used for credentialed vulnerability scanning where the credentials are one time use. This ensure the credentials no longer work after some set of criteria, though this solution also usually costs some amount of money. If you can't use a PAN solution, you can also do a set time period where a scan happens.
- **pfSense** - Open source firewall solution. You can add logging, normal firewall rules, etc.
- **PLC** - Programmable Logic Controller. Computer designed for industrial settings. Think about manufacturing.
- **PUA** - Privileged User Agreement. Code of conduct for high privileged employees with access to sensitive data etc.
- **Qualys** - Cloud-based vulnerability management software. With installed sensors on base machines.
- **RBAC** - Role-Based Access Control. Resources are protected by ACLs, managed by administrators. Think Windows groups.
- **Reaver** - Wireless tool to attack WPS enabled networks. Can potentially crack a WPS pin (which is 8 digits long) within hours as long as it's not rate-limited.
- **Red Team** - The attackers or pentesters that try to offensively attack a system. Contrast with the blue team.
- **RFC** - Request For Change. What is sounds like - a document that gives the reason for a change and how to implement that change.
- **ROT** - Root of Trust. Crypto module (hardware) embedded into a computer system that can endorse trusted execution. Think TPM module in your computer.
- **RPO** - Recovery Point Objective. Longest time an organization can tolerate lost data being recoverable. Ex. a database goes down, and new data isn't recorded for 12 hours. That 12 hours is the RPO, and is that tolerable to the organization?
- **RSOI** - Return on Security Investment. By adding this security control, what's the expected return? This is a ratio.
- **RTO** - Recovery Time Objective. The time between systems going down to when it can be up again. Ex, if live databases all go down, how long does it take for them to recover?
- **RTOS** - Real Time Operating System. Prioritizes deterministic execution of operations to ensure consistent responses. Can't tolerate downtime - can't be down.
- **Runbook** - Automated version of a playbook.
- **Sanitization** - Procedures that define how to dispose information or objects.
- **SCADA** - Supervisory Control and Data Acquisition. Industrial control system (ICS) that manages large-scale, multiple-site devices and equipment spread across some geographic location.
- **Scan-Patch-Scan** - A common motto for IT - scan for vulnerabilities, patch it, then scan it again to verify the patch.
- **SCAP** - A NIST framework that outlines various accepted practices for automating vulnerability scanning. This also sets the standard for the format the results/vulnerabilities come in.
- **SDN** - Software Defined Networks. Use software to define physical networks. Also similar to "Code as Infrastructure."
- **Separation of Duties** - Checks and balances on processes.
- **Sigcheck** - Sysinternals utility that lets you verify local root certs with Microsoft's master trust list.
- **SLA** - Service Level Agreement. A contractual agreement, contrast this to MOU. This is a legal contract, if someone offers a 99.9% uptime and only delivers 99% uptime, there could be monetary penalties built into the SLA.
- **SLE** - Single Loss Expectancy.
- **SNORT** - Open source IDS. 
- **SSO** - Single Sign On. One password to rule them all.
- **SOAR** - Security Orchestration, Automation, Response, basically think of this as a "next-gen" SIEM.
- **SoC** - System on a chip. Efficient by combining different components on the same chip. Think single board computers like Raspberry Pi.
- **SOX** - Sarbanes-Oxley Act. Rules that define storage and retention requirements for publicly traded companies.
- **SPF** - Sender Policy Framework. In emails, this can be used to verify the sender of an email is indeed on the IP list. Once an SFP record is setup, the email service will check the domain (ex. me@thomaszhang.com, so it'll check thomaszhang.com) for a txt record containing the IP addresses that's allowed. If the email came from an allowed IP address, that's likely legitimate. Read more [here](https://www.courier.com/guides/dmarc-vs-spf-vs-dkim/).
- **Tabletop Exercises** - Simulated emergency situation on a table. But the downside is that the people don't go through the entire flow.
- **TPM** - Trusted Platform Module. A secure hardware store of digital certificates, keys, hashed passwords, etc. These generally exist on all modern day computers. In fact, this is a requirement to install Windows 11.
- **UEFI** - Unified Extensible Firmware Interface. During boot, this may show (on your 64 bit computer) with a full GUI and mouse/keyboard support. This runs at the firmware level (without an operating system).
- **VPN** - Virtual Private Network. Uses authentication/authorization to control access. Uses an encrypted connection to some other network. This should be a familiar concept.
- **Vulnerability Management Lifecycle** - Assessment, Prioritization, Act, Reassessment, Improvement. See more [here](https://heimdalsecurity.com/blog/vulnerability-management-lifecycle/) and [here](https://www.crowdstrike.com/cybersecurity-101/vulnerability-management/vulnerability-management-lifecycle/)
- **White Team** - The team that supervises/administers/supports the blue/red team in the incident response training.
- **WRT** - Work Recovery Time. Fixing the secondary effects after RTO period. Ex. if live databases go down, and critical functions are working, how long does it take to ensure analytics are back up.