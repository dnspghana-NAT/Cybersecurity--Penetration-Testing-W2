# Cybersecurity--Penetration-Testing Report-W2

#PENETRATION TESTING REPORT

##FOOTPRINTING & NETWORK SCANNING PHASES

|Cybersecurity| Week -Two Project Module| Networkwalks|

|Pentester Name (Cybersecurity professional) |Nathaniel Apuru Avaraako|
|---------------|-----------------------|
|Program/Batch Program/Batch|	B082-Networkwalks|
|Modules Completed|W2-PM1 (Multiple Kali Tools) W2-PM5 (Zenmap Scanning) | 
|Target Client	 |Networkwalks (written permission secured and obtained) My local LAN Network|
|Permission secured from Target Client| Permission obtained|
|Project Scope/phases covered| Phase1: Reconnaissance & Foot printing. Phase2: Scanning & Network Discovery|
 
*#Liability Disclaimer*

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. I did not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

 
*#General Background and Introduction*

This report covered footprinting the networkwalks.com domain using multiple Kali Linux tools as specified in TOR (W2-PM1) and scanning the local network with Zenmap as referenced in (W2-PM5). The project Module one (1) covers footprinting  and  scanning phase. This together show how public information will be gathered by mapping live hosts on the target network. This was part of ongoing internship program at Networkwalks categorized as week two (W2).
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the results observed were displayed as screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

*#The Scope of Tools use and the Purpose*

The table below show the types of tools used in the process and their respective purpose
|Tools                                                             | Purpose                                     |
|------------------------------------------------------------------|----------------------------------------------|
|Kali Linux & Windows                                              |Operating systems used for reconnaissance activities|
|WHOIS                                                        |WHOIS	Find domain registration details (owner, dates, name servers).|
|whatweb                                                       |whatweb	Fingerprint web technologies (server, CMS, plugins, IP).|
|nslookup                                                          |Resolve the domain name to its IP address using DNS.|
|curl -I                                                           |Read the HTTP response headers of the website.|
|wafw00f                                                         |wafw00f	Detect whether a Web Application Firewall protects the site.|
|dnsrecon                                                   |dnsrecon	Enumerate all DNS records (NS, MX, SPF, TXT, SRV).|
|Zenmap (Nmap GUI)                   |Scan the local subnet to find live hosts, IPs and MAC addresses.|
|Windows CMD|Local IP and MAC address identification|


