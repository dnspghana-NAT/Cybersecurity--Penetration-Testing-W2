# Cybersecurity--Penetration-Testing Report-W2

## PENETRATION TESTING REPORT

## FOOTPRINTING & NETWORK SCANNING PHASES

|Cybersecurity| Week -Two Project Module| Networkwalks|

|Pentester Name (Cybersecurity professional) |Nathaniel Apuru Avaraako|
|---------------|-----------------------|
|Program/Batch Program/Batch|	B082-Networkwalks|
|Modules Completed|W2-PM1 (Multiple Kali Tools) W2-PM5 (Zenmap Scanning) | 
|Target Client	 |Networkwalks (written permission secured and obtained) My local LAN Network|
|Permission secured from Target Client| Permission obtained|
|Project Scope/phases covered| Phase1: Reconnaissance & Foot printing. Phase2: Scanning & Network Discovery|
 
# Liability Disclaimer

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. I did not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

# WEEK 2 PROJECT MODULE 1

## RECONAISSANCE AND FOOTPRINTING SIX KALI LINUX TOOLS

**General Background and Introduction**

This report covered footprinting the networkwalks.com domain using multiple Kali Linux tools as specified in TOR (W2-PM1) and scanning the local network with Zenmap as referenced in (W2-PM5). The project Module one (1) covers footprinting  and  scanning phase. This together show how public information will be gathered by mapping live hosts on the target network. This was part of ongoing internship program at Networkwalks categorized as week two (W2).
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the results observed were displayed as screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

## The Scope of Tools use and the Purpose**

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

1. ## ACTIVITIES PERFORMED UNDER THE MODULES

   ## Footprinting & Reconnaissance**

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

![wafw00f screenshot](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/ecb2de96e47908cdd21bb0a62b17ce38bde2dea9/SCREENSHOT%20WAFW00F%20OUTPUT%20AS%20KALI%20TOOL.PNG)

5.2 **How is the information revealed useful to an attacker**

     *wafw00f tells an attacker if a firewall is watching
     *Here the site sits behind ModSecurity (SpiderLabs).
     * Knowing a WAF is present shapes the whole attack
     *Naive attempts will be blocked or logged, so the attacker must adapt or try to bypass it.

6.0 **Enumerate all DNS records: name servers, mail servers, SPF, TXT and service (SRV) records**
6.1 **dnsrecon** command 
Here I entered this: dnsrecon -d networkwalks.com and the displayed was shown below

![Screenshot of dnsrecon](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/1bc18df97991834063525987e10e660e4085d3e7/SCREENSHOT%20DNSRECON%20AS%20OUTPUT%20KALI%20TOOL.PNG)

6.2 **How is the information revealed useful to an attacker**

      *dnsrecon maps the target's entire DNS footprint:
      * mail servers, 
      *DNS software version (Bind 9.16.23), 
       *SPF policy  
       *CPanel service records.
       * Each record is a potential foothold and helps an attacker understand the email and hosting setup

Conclusively on the project module one,  footprinting and Reconnaissance is crucial because Reconnaissance is the first stage of every real attack. Before touching a target, an attacker quietly builds a complete profile of it using only public information, exactly the
tools in this task. whois and DNS tools (nslookup, dnsrecon) reveal who owns the domain, its real IP address, its hosting provider and its mail servers. whatweb and curl fingerprint the exact software and versions running, which an attacker matches against known vulnerabilities. wafw00f warns them whether a firewall is watching, so they know how careful to be.None of these tools attack the target. They only read what is already public, which is exactly why footprinting is so powerful and so hard to detect. The more an organization leaks, the easier every later stage of the attack becomes. This is also why defenders run the same tools on themselves: to see what an attacker would see, and to reduce it. 

# WEEK 2 PROJECT MODULE 5

## NETWORK SCANNING WITH ZENMAP

**Background**

Zenmap is the official GUI version of Nmap which can be used on Windows PC. It is a security scanner software tool which is used by Cybersecurity professionals & Hackers. It is a multi-platform (Linux, Windows, Mac OS X, BSD, etc.) free and open source application which aims to make Nmap easy for beginners to use while providing advanced features for experienced Nmap users. Frequently used scans can be saved as profiles to make them easy to run repeatedly.
op
2.**# ACTIVITIES PERFORMED UNDER THE MODULES 5**

2.1 **Activity**: Download & install Zenmap from official website on your Windows PC
      What was done: Zenmap was downloaded from the official website on the windows computer through: https://nmap.org/download.html and installed as shown below:

   ![Zenmap installing process](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/b6410fd8d857df51ee7fe8b0bf5d452f10d1d337/zenmap%20installing%20process.PNG)
      
2.2  **Activity**: Find your local IP address & your LAN subnet 
      what was done: I Opened CMD & run ipconfig command to find your PC’s local IP address & 
your local LAN subnet as displayed below:

![Ipconfig command](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/8d82f943029e4116818cabe197bb4b208b531fa6/cmd%20ipconfig.PNG)
      
2.3  **Activity**:  Find the list of live hosts/PC’s in your IP subnet
      what was done: I Opened Zenmap, input the local LAN subnet & select Ping Scan to find the list of 
live hosts in your subnet as shown below:

![Zenmap ping scan](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/eb7760dba2d7761e410aef415fbf98c6fd92a377/Zenmap%20ping%20scan.PNG)
      
2.4  **Activity**: How many hosts are live in your subnet?
      what was done:
      I scanned the local subnet and found five live host.
2.5  **Activity**: What are the IP addresses of the live hosts?
       
       what was done:
       The following were the IP addresses found
       *10.0.0.1
       *10.0.0.2
       *10.0.0.3
       *10.0.0.6
       *10.0.0.10
       
2.6   **Activity**: What are the MAC addresses of the live hosts?
        
        what was done: 
        I scan the network and the following were the MAC addresses found:
        *52:54:00:12:35:00 
        *08:00:27:58:A4:59 
        *52:54:00:12:35:00 
        *08:00:27:5A:87:BC
2.7   **Activity**: Display & save the output topology in PDF Format on your desktop
        what was done: I scanned the network and the topology shown below:
![network topology](https://github.com/dnspghana-NAT/Cybersecurity--Penetration-Testing-W2/blob/769ba7d18f93ee22c42b5a3c55855af4c8743dbf/Zenmap%20topology.PNG)
## Risk and Impact Analysis

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks. as depicted in the table below:
|#    |#	Risk/Finding|Evidence/Observation|Potential Impact|	Risk Level|
|-----|--------------|--------------------|-----------------|-----------|
|1     |Web technology information exposed|WhatWeb identified WordPress and WP Download Manager|Attackers may use exposed technology/version information to identify software requiring further security review|● Medium|
|2|Server IP address identifiable|2	Server IP address identifiable	Nslookup resolved the domain to 192.232.216.135|	Provides information about the network location of the web service|	● Low|
|3|HTTP technical information exposed|Curl returned HTTP response headers and exposed /wp-json/|May assist technology fingerprinting and further enumeration|● Low|
|4|WAF technology identifiable|Wafw00f identified ModSecurity (SpiderLabs)|	Reveals information about the web application’s security architecture|	● Low|
|5|DNS infrastructure information exposed|DNSRecon identified DNS, mail and service-related records|DNS information can help build a broader infrastructure profile|● Medium|
|6|Multiple live hosts visible on local network|Zenmap identified four live hosts in the example network|Unknown or unauthorized devices may potentially be present on a network|● Medium|

The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.
The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules. Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

## Recommendations
Based on the observations from these activities, I recommend the following security improvements:
1.	Review publicly exposed technology information
Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.
2.	Keep software updated
CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.
3.	Review HTTP headers
HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.
4.	Review DNS records regularly
DNS records should be checked periodically to ensure that only required information and services are publicly exposed.
5.	Properly configure and monitor the WAF
Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.
6.	Perform regular internal network discovery
Organizations should periodically scan their own networks to identify active devices.
7.	Investigate unknown devices
Any unexpected device discovered during network scanning should be investigated and verified.
8.	Maintain network documentation
Network topology and device information should be documented and updated regularly.
9.	Perform security testing with authorization
Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

7. ## Conclusion
During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.
In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.
In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.
The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.
I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.
Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

