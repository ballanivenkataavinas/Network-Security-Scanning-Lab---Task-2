# Day 13 - Reconnaissance (Information Gathering Phase)

-- Started Task 2: Network Security & Scanning  

-- Learned about Reconnaissance (Recon):
   -- First phase of cybersecurity assessment  
   -- Collect information about target systems  

Types of Reconnaissance
-- Passive Recon:
   -- No direct interaction with target  
   -- Safe and untraceable  

-- Active Recon:
   -- Direct interaction with target  
   -- Can be detected  

Passive Recon Techniques
-- Used tools/concepts:

   -- Whois → domain registration details  
   -- Nslookup → DNS information  
   -- Google Dorking → advanced search queries  

 Practical Commands

-- Checked domain info:

   whois example.com  

-- DNS lookup:

   nslookup example.com  

Active Recon Techniques

-- Performed network probing  

-- Used ping sweep to check live hosts:

   ping 192.168.x.x  

-- Understood banner grabbing:
   -- Collects service information from open ports  

 Key Concepts Learned

-- Recon is critical before launching any scan or attack  
-- Passive recon is stealthy  
-- Active recon provides more detailed information  
-- Attackers use recon to identify targets and weaknesses  

 Security Insights

-- Publicly available data can expose sensitive information  
-- Organizations must limit exposed information  
-- Monitoring unusual probing activity is important  

-- All activities performed in controlled and ethical lab setup  


# Day 14 - Network Scanning using Nmap

-- Performed network scanning using Nmap to identify live hosts, open ports, and running services  

Tool Used

Basic Scan

-- Scanned target system (Metasploitable2):

   nmap <target-ip>

-- Purpose:
   -- Identify open ports  
   -- Detect active services  

TCP SYN Scan (Stealth Scan)

-- Command:

   nmap -sS <target-ip>

-- Explanation:
   -- Half-open scan (stealthy)  
   -- Faster and less detectable  

TCP & UDP Scan

-- Command:

   nmap -sS -sU <target-ip>

-- Purpose:
   -- Scan both TCP and UDP ports  

Service Version Detection

-- Command:

   nmap -sV <target-ip>

-- Output shows:
   -- Service name  
   -- Version information  

OS Detection

-- Command:

   nmap -O <target-ip>

-- Purpose:
   -- Identify operating system of target  

Aggressive Scan (Full Info)

-- Command:

   nmap -A <target-ip>

-- Includes:
   -- OS detection  
   -- Version detection  
   -- Script scanning  
   -- Traceroute  

Port Range Scan

-- Command:

   nmap -p 1-1000 <target-ip>

-- Purpose:
   -- Scan specific port range  

Save Scan Results

-- Command:

   nmap -oN scan.txt <target-ip>

-- Output saved for reporting  

Key Concepts Learned

-- Open Port:
   -- Entry point for communication  

-- Closed Port:
   -- Not accepting connections  

-- Filtered Port:
   -- Blocked by firewall  

Security Insights

-- Open ports can expose services to attackers  
-- Outdated services may contain vulnerabilities  
-- Regular scanning helps detect security risks  

# Day 15 - Service Enumeration

-- Performed service enumeration to gather detailed information about running services on the target system  

Tools Used

What is Service Enumeration?

-- Process of extracting detailed information about services running on open ports  
-- Helps identify:
   -- Service versions  
   -- Misconfigurations  
   -- Potential vulnerabilities  

Step 1 – Identify Services (Using Nmap)

-- Command:

   nmap -sV <target-ip>

-- Output Includes:
   -- Port number  
   -- Service name  
   -- Version details  

Step 2 – Banner Grabbing (Manual Enumeration)

-- Using Netcat:

   nc <target-ip> <port>

-- Example:

   nc <target-ip> 21

-- Purpose:
   -- Retrieve service banner  
   -- Identify software & version  

Step 3 – Web Server Enumeration

-- Using Nikto:

   nikto -h http://<target-ip>

-- Finds:
   -- Outdated server software  
   -- Security misconfigurations  
   -- Known vulnerabilities  

Step 4 – Enumerate Specific Ports

-- FTP (Port 21):

   nmap -p 21 --script ftp-anon <target-ip>

-- SSH (Port 22):

   nmap -p 22 --script ssh-hostkey <target-ip>

-- HTTP (Port 80):

   nmap -p 80 --script http-title <target-ip>

Step 5 – Detailed Enumeration (Nmap Scripts)

-- Command:

   nmap --script vuln <target-ip>

-- Purpose:
   -- Detect known vulnerabilities automatically  

Key Concepts Learned

-- Banner Grabbing:
   -- Extracts service information from open ports  

-- Enumeration:
   -- Deep inspection of services  

-- Service Version:
   -- Helps identify exploitable vulnerabilities  

Security Insights

-- Outdated services are major security risks  
-- Misconfigured services can expose sensitive data  
-- Enumeration is crucial before exploitation  

# Day 16 - Vulnerability Scanning

-- Performed vulnerability scanning to identify security weaknesses in the target system  

Tools Used

What is Vulnerability Scanning?

-- Process of identifying known security weaknesses in systems and services  
-- Helps detect:
   -- Outdated software  
   -- Misconfigurations  
   -- Known CVEs  

Step 1 – Nmap Vulnerability Scan

-- Command:

   nmap --script vuln <target-ip>

-- Purpose:
   -- Runs vulnerability detection scripts  
   -- Identifies known issues automatically  

Step 2 – Targeted Vulnerability Scripts

-- Example Commands:

   nmap --script ftp-vuln* <target-ip>  
   nmap --script http-vuln* <target-ip>  

-- Focus:
   -- Service-specific vulnerabilities  

Step 3 – Web Vulnerability Scan (Nikto)

-- Command:

   nikto -h http://<target-ip>

-- Detects:
   -- Dangerous files  
   -- Server misconfigurations  
   -- Outdated web server versions  

Step 4 – Analyze Scan Results

-- Look for:
   -- Vulnerable service versions  
   -- Exposed endpoints  
   -- Weak configurations  

Key Concepts Learned

-- CVE (Common Vulnerabilities and Exposures):
   -- Publicly disclosed vulnerabilities  

-- False Positives:
   -- Not all detected issues are exploitable  

-- Risk Identification:
   -- Prioritizing vulnerabilities based on severity  

Security Insights

-- Regular vulnerability scanning is critical  
-- Early detection prevents exploitation  
-- Systems must be patched and updated  

# Day 17 - Packet Analysis using Wireshark

-- Performed network packet analysis to inspect and understand real-time traffic  

Tool Used

What is Packet Analysis?

-- Process of capturing and inspecting network traffic  
-- Helps understand:
   -- Data flow  
   -- Protocol behavior  
   -- Suspicious activity  

Step 1 – Start Packet Capture

-- Open Wireshark  
-- Select active network interface (e.g., eth0 / wlan0)  
-- Start capturing packets  

Step 2 – Apply Filters

-- HTTP traffic:

   http

-- DNS traffic:

   dns

-- TCP traffic:

   tcp

-- Purpose:
   -- Focus on specific types of traffic  

Step 3 – Analyze Packets

-- Observed:
   -- Source IP & Destination IP  
   -- Protocol used (TCP, UDP, HTTP, DNS)  
   -- Packet length & data  

Step 4 – Follow TCP Stream

-- Right-click packet → Follow → TCP Stream  

-- Purpose:
   -- View complete communication between two systems  

Step 5 – Identify Suspicious Activity

-- Look for:
   -- Unusual traffic patterns  
   -- Unknown IP addresses  
   -- Repeated failed requests  

Key Concepts Learned

-- Packet:
   -- Small unit of data transmitted over network  

-- Protocol:
   -- Rules for communication (TCP, UDP, HTTP)  

-- Sniffing:
   -- Capturing network traffic  

Security Insights

-- Unencrypted traffic can expose sensitive data  
-- Packet analysis helps detect attacks and anomalies  
-- Monitoring network traffic improves security  
  
