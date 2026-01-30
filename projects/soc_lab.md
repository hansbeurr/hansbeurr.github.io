---
layout: project
type: project
image: img/vacay/vacay-square.png
title: "Home Lab SOC"
date: 2025
published: true
labels:
  - Cybersecurity
  - Elk Stack
  - Virtualization
  - Linux
summary: "Creating a Virutal Security Operations Center to detect and analyze mock cyberattacks."
---
---


As I work toward becoming an ethical hacker, I wanted to see the "other side" of cybersecurity. I built a virtual Security Operations Center (SOC) to learn how defenders find and stop hackers. This project helped me move past just reading about attacks. Instead, I built a real system that can collect and show security data as it happens. For this project, I set up several virtual computers on my own machine. I used a Kali Linux computer as the "Attacker" and a Windows 11 computer as the "Victim." Every move the attacker made—like trying to guess a password or running a malicious file—was sent to a central system called a SIEM. This system acted like a security camera for the network, letting me see exactly how an attack looks to a defender.

<img src="../img/soc_lab/soc_lab_home.png">

```
Barebones Lab due to limited hardware
SOC-Machine: Ubuntu LTS Server
Vulnerable Machine: Windows 7 (Stuxbot Vunerable)
```

## Home Page
<img src="../img/soc_lab/stuxbot.png">

## Lateral Transfer Tool Detection
<img src="../img/soc_lab/lateral_transfer.png">

*This query monitors Sysmon Event ID 11 to detect file creation events within the C:\Users\Public directory, a very common "staged" location to use.
We find an application called <a href ="https://jumpcloud.com/it-index/what-is-rubeus">Rubeus</a> known for lateral movement and privelage escalation.*

<img src="../img/soc_lab/win_rm_lateral.png">

*This query monitors PowerShell Event ID 4104 (Remote Command Execution) to detect the use of the Enter-PSSession command, which indicates an adversary is attempting Lateral Movement to remotely control another machine on the network.*


