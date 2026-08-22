**# Cybersecurity--Penetration-Testing Report-W2**

**# PENETRATION TESTING REPORT**

**## FOOTPRINTING & NETWORK SCANNING PHASES**

|Cybersecurity| Week -Two Project Module| Networkwalks|

|Pentester Name (Cybersecurity professional) |Nathaniel Apuru Avaraako|
|---------------|-----------------------|
|Program/Batch Program/Batch|	B082-Networkwalks|
|Modules Completed|W2-PM1 (Multiple Kali Tools) W2-PM5 (Zenmap Scanning) | 
|Target Client	 |Networkwalks (written permission secured and obtained) My local LAN Network|
|Permission secured from Target Client| Permission obtained|
|Project Scope/phases covered| Phase1: Reconnaissance & Foot printing. Phase2: Scanning & Network Discovery|
 
**# Liability Disclaimer**

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. I did not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

 
**# General Background and Introduction**

This report covered footprinting the networkwalks.com domain using multiple Kali Linux tools as specified in TOR (W2-PM1) and scanning the local network with Zenmap as referenced in (W2-PM5). The project Module one (1) covers footprinting  and  scanning phase. This together show how public information will be gathered by mapping live hosts on the target network. This was part of ongoing internship program at Networkwalks categorized as week two (W2).
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the results observed were displayed as screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

**# The Scope of Tools use and the Purpose**

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

**# ACTIVITIES PERFORMED UNDER THE MODULES**

**## Footprinting & Reconnaissance**

I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target. The strategies and procedures used to gather the target network information include the following:

1.0 **Activity**: *Query the public domain registration record to find who owns the domain, when it 
was registered, and its name servers*
1.1 **WHOIS** command.
   I entered this **whois networkwalks.com**  by opening terminal in Kali  and the output of the was displayed as shown below:

  ![Screenshot of whois command](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/1473547c2dae378a8769729e23cf60457dbaf5d9/SCREENSHOT%20WHOIS%20OUTPUT.PNG)
1.2 **How is the above revealed information useful to an attacker**

        * whois reveals the registrar, registration and expiry dates, and name servers of networkwalks.com.  
        * Here the name servers point to HostGator, so any attacker instantly learns the hosting provider. 
        * Registration dates and abuse contacts help with social engineering and planning

2.0 **Activity**: Fingerprint the technologies running on the website: web server, CMS, plugins, 
framework and IP address.

2.1 **whatweb** command
   I entered this **whatweb networkwalks.com** by opening the Kali terminal and the output was the result displayed below:

 ![Screenshot of whatweb command](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/414095d1217c44cf9a87107bda003b834316755c/SCREENSHOT%20WHATWEB%20OUTPUT.PNG)
2.2 **How is the above revealed information useful to an attacker**

    * whatweb exposes the exact software and versions for instants it shows this domain uses WordPress 7.0.4 and WP Download Manager 3.3.58)
    * An attacker looks at these versions up in vulnerability databases to find known exploits.
    * It also leaks the server IP and an email address which the attacker can leverage on to explore the target network
    
3.0 **Activity**: Resolve the domain name to its IP address using DNS

3.1 **nslookup** command 
I entered this: **nslookup networkwalks.com** by accessing the Kali terminal and the output was the information displayed below:

![Screenshot of nslookup](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/1cc1d81e61321704989264100464bdadec65f661/SCREENSHOT%20NSLOOKUP%20AS%20KALI%20TOOL.PNG)

3.2 **How is the information revealed useful to an attacker**
   
    *nslookup turns a domain name into its real IP address (192.232.216.135) as shown above
    * Knowing the IP an attacker scans the server directly
    * Look up other sites on the same IP, and map the target's infrastructure
4.0 **Activity**: Read the HTTP response headers to see the server banner, status, cookies and redirects  

4.1 **Curl -1** command
I entered this: curl -I https://networkwalks.com by accessing the Kali terminal interface and the output was the screenshot shown below:

![Screenshot of Curl-I](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/d685469f39f9c0fd06e98abbf0d4fe57d90a45ce/SCREENSHOT%20CURL-I%20OUTPUT%20AS%20KALI%20TOOL.PNG)

4.2 **How is the information revealed useful to an attacker**
      
       *HTTP headers leak the web server
       *Caching stack and hidden endpoints (like the WordPress REST API at /wp-json/)
       * Attackers read headers to fingerprint the stack and find entry points without even loading the full page.

5.0 **Activity**: Detect whether a Web Application Firewall (WAF) is protecting the target site.
5.1 **wafw00f** command
Here I opened the Kali terminal entered this: wafw00f networkwalks.com and the output was what shown in the screenshot below:
![]()
