# Investigating Suspicious Network Traffic & SIEM Use Cases  

This repository documents hands-on Blue Team labs as part of my **#100DaysOfCybersecurity** journey.  
The focus is on network traffic analysis, log investigation, and building detection rules in SIEMs.  

---

## 🔹 Lab 1: Investigating Suspicious Network Traffic (Day 30)  

### Objective  
Simulate network activity between attacker, target, and client machines. Capture and analyze traffic.  

### Lab Setup  
- **Kali Linux (Attacker)** – 192.168.1.4  
- **Ubuntu VM (Target)** – 192.168.1.5 (running SSH)  
- **Windows Host (Client)** – 192.168.43.39  

### Steps  
1. Performed a **TCP SYN scan** from Kali → Ubuntu:  
   ```bash
   nmap -sS -p 1-1000 192.168.1.5

2. Sent ICMP pings between hosts.
3. Captured all activity using **Wireshark** and saved to `capture.pcap`.
4. Observed:

   * Open port 22 (SSH)
   * Multiple ping requests/replies
   * Normal vs suspicious traffic baseline

---

## 🔹 Lab 2: Simple Network Diagram (Day 31)

### Objective

Visualize the lab environment.

**Hosts**

* Windows Host → Client workstation
* Ubuntu VM → Target server (SSH service)
* Kali VM → Attacker / Test box

A simple 3-node diagram was created (Windows ↔ Ubuntu ↔ Kali).

---

## 🔹 Lab 3: SIEM Basics (Day 32–43)

### Objective

Move from raw traffic analysis to **log detection** using a SIEM.

### Covered Topics

* **Day 32** – What is a SIEM?
* **Day 33** – Introduction to Logs (what, why, where)
* **Day 34** – Reading Windows Logs
* **Day 35** – Reading Linux Logs
* **Day 36** – Log Sources (Syslog, Auth logs, App logs)
* **Day 37** – Detecting Unauthorized Access
* **Day 38** – Introduction to Splunk (Free Tier)
* **Day 39** – Introduction to ELK Stack (Elastic SIEM)
* **Day 40–43** – Building SIEM Detection Rules (Failed logins, USB insertions, PowerShell abuse)

### Example Queries

**ELK (Kibana Query Language)**

```kql
system.auth.ssh.event: failed
```

**Splunk Search**

```spl
index=linux_logs "Failed password"
```

---

## 📂 Repository Structure

```
├── capture.pcap              # Network traffic capture (Day 30)
├── map.png                   # Simple network diagram (Day 31)
├── detections/
│   ├── elk_failed_login.txt  # KQL query example
│   ├── splunk_failed_login.txt
│   └── sigma_rules.yml
├── README.md                 # Documentation (this file)
```

---

## 🚀 Next Steps

* Add more detection rules (PowerShell abuse, USB insertion, privilege escalation).
* Expand labs into **incident response scenarios**.
* Continue through the 100-day roadmap.

---

## 📌 Notes

This repo is part of my **#100DaysOfBlueTeam** journey.
Follow my progress on [LinkedIn](https://www.linkedin.com/in/joseph-oyedepoa) and here on GitHub.


