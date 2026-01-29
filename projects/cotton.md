---
layout: project
type: project
image: img/cotton/cotton-square.png
title: "Port Scanner Script"
date: 2025
published: true
labels:
  - CTF
  - Python
  - Script
summary: "A script for streamlining using nmap during a certification course."
---

<img class="img-fluid" src="../img/cotton/cotton-header.png">

During CTFs enumeration is almost always often 90% of the challenge and with that I created a script that streamlined nmap to be less clunky in my opinion.
Here is a snippet of the script that goes through the some of the common ports that are  

```def analyze_results(nm):

    # Iterate over all hosts found
    for host in nm.all_hosts():
        print(f"***********************************************")
        print(f"Host: {host} ({nm[host].hostname()})")
        print(f"State: {nm[host].state()}")
        
        # for loop to check all the ports whether TCP or UDP
        for proto in nm[host].all_protocols():
            print(f"\nProtocol: {proto.upper()}")
            
            # sort the found ports 
            lport = nm[host][proto].keys()
            
            for port in sorted(lport):
                state = nm[host][proto][port]['state']
                product = nm[host][proto][port]['product']
                version = nm[host][proto][port]['version']
              
                service_info = f"{product} {version}".strip()
                print(f"  Port: {port:<5} | State: {state:<6} | Service: {service_info}")

                # list the usual suspects for vulenrabilites
                if port == 80 or port == 443:
                    print(f"    [!] Web Server detected - Check for HTTP/HTTPS vulnerabilities.")
                elif port == 445:
                    print(f"    [!] SMB detected - Check for EternalBlue or NULL Session.")
                elif port == 3389:
                    print(f"    [!] RDP detected - Check for BlueKeep or Default Creds.")
        
        print(f"***********************************************")
```  


