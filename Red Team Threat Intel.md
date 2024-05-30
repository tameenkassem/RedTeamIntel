# Red Team Threat Intel
## TryHackMe Rooms


## Introduction

- Threat Intelligence (CTI) or Tactics, Techniques and Procedures (TTPS) are used by defenders to aid in detection measures.
- Information and Sharing Analysis Centers (ISACS) collect indicators of Compromise (IoCs) and TTPS, and maintain them, allowing for frameworks to plot out overarching timelines of suspicious activities/compromise.
- Specifically, cyber frameworks collect and categorize TTPS based on varying characteristics:
    - Threat Group
    - Kill Chain Phase
    - Tactic
    - Objective/Goal
- Leveraging TTPS is used for planning, rather than engagement execution. In the event of engagement, the red team will use threat intelligence to create tools, modify traffic and behavior, and emulate targeted adversary.
    - The red team uses threat intel to emulate behaviors of adversaries, relying on collected TTPS and IOCs.

##TIBER-EU Framework
https://imgur.com/5z9TO1G

Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]
h tags
> or formatting instructions.



## TTP MAPPING
- Employed by red cell, mapping TTPs to a kill chain aids in planning an engagement for adversary emulation.
- The adversary can be chosen based on:
    - Target industry
    - Employed Attack Vectors
    - Country of Origin
    - Other Factors



## MITRE ATT&CK
- Important cyber framework that provides IDs and descriptions of categorized TTPs.

1. Reconnaissance:
- No identified TTPs, use internal team methodology
2. Weaponization:
- Command and Scripting Interpreter
- PowerShell
- Python
- VBA
- User executed malicious attachments
3. Delivery:
- Exploit Public-Facing Applications
- Spearphishing
4. Exploitation:
- Registry modification
- Scheduled tasks
- Keylogging
- Credential dumping
5. Installation:
- Ingress tool transfer
- Proxy usage
6. Command & Control:
- Web protocols (HTTP/HTTPS)
- DNS
7. Actions on Objectives
- Exfiltration over C2

Read the above and use MITRE ATT&CK Navigator to answer the questions below using a Carbanak layer.
https://attack.mitre.org/groups/G0096/
1.How many Command and Control techniques are employed by Carbanak?
A: 2
2.What signed binary did Carbanak use for defense evasion?
A: Rundll32
3.What Initial Access technique is employed by Carbanak? 
A: Valid Accounts
## Mapping it out


| Cyber Kill Chain | MITRE ATT&CK |
| ------ | ------ |
| Recon | Reconnaissance |
| Weaponization | Execution |
| Delivery | Initial Access|
| Exploitation | Initial Access |
| Installation | Persistence / Defense Evasion |
| Command & Control |  Command and Control |
| Actions on Objectives | Exfiltration / Impact |

https://imgur.com/a/cwSjva4

Open the provided ATT&CK Navigator layer and identify matched TTPs to the cyber kill chain. Once TTPs are identified, map them to the cyber kill chain in the static site.

To complete the challenge, you must submit one technique name per kill chain section.

Once the chain is complete and you have received the flag, submit it below.

Flag: THM{7HR347_1N73L_12 _4w35om3}

Answer questions below relating to needed engagement resources.

1. What web shell is APT 41 known to use? 
ASPXSpy
2. What LOLBAS (Living Off The Land Binaries and Scripts) tool does APT 41 use to aid in file transfers? 
certutil
3. What tool does APT 41 use to mine and monitor SMS traffic? 
MESSAGETAP
## Development


#### headers


## headers



## headers


