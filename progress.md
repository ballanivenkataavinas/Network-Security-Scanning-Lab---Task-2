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

