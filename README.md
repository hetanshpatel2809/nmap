# Network Reconnaissance & Port Scanning Report

## 🎯 Project Objective
The goal of this project was to perform authorized network reconnaissance on a target system using Nmap. The objectives included resolving domain names to IP addresses, identifying active hosts, scanning for open ports, and mapping potential attack surfaces.

> 🛑 **Disclaimer:** This scan was performed strictly for educational purposes on an authorized, publicly available testing target provided by Nmap (`scanme.nmap.org`). Unauthorised scanning of external networks can be illegal.

---

## 🛠️ Tools & Environment
* **Operating System:** Kali Linux (Virtual Machine)
* **Tool Used:** Nmap (Network Mapper) v7.9x
* **Target:** `scanme.nmap.org`

---

## 🚀 Step-by-Step Methodology & Findings

### Step 1: Target Identification & Ping Sweep
Before scanning specific ports, I resolved the target domain name to its public IP address and checked if the host was active.
* **Command:** `nmap -sn scanme.nmap.org`
* **Resulting IP Address:** `45.33.32.156`


### Step 2: Comprehensive Port & Service Scanning
I executed a Service Version detection scan against the top 1000 standard ports to see exactly what services were running on the target.
* **Command:** `nmap -sV -F 45.33.32.156`
* **Key Flags Used:**
  * `-sV`: Detects service/version information.
  * `-F`: Fast mode (scans fewer ports for quick results).


### Step 3: Result Analysis
The scan successfully uncovered the following open ports:
* **Port 22/tcp (SSH):** Running OpenSSH (Version X.X). This port allows remote command-line access.
* **Port 80/tcp (HTTP):** Running Apache httpd (Version X.X). This hosts the public web server.

---

## 🛡️ Defensive Remediation Recommendations
Based on the reconnaissance findings, a network administrator should implement the following security controls:
1. **Disable Unnecessary Services:** If Port 9929 is not actively required for business operations, it should be disabled to reduce the attack surface.
2. **Secure SSH Access:** Restrict Port 22 access using firewall rules (IP whitelisting) and enforce multi-factor authentication (MFA) instead of password logins.
3. **Deploy a Firewall:** Block inbound ICMP (ping) echo requests if stealth is desired, though this target is designed to be public.
