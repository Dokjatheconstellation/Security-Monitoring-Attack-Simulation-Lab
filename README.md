# Enterprise-Grade Security Monitoring & Attack Simulation Lab

A fully virtualized, self-contained corporate network environment designed to simulate real-world cyberattacks and monitor them in real time. This project demonstrates the practical implementation of an automated Security Operations Center (SOC) workflow, bridging the gap between offensive tactics (Red Teaming) and defensive monitoring (Blue Teaming).

---

## 🏗️ Architecture & Topology

The lab environment isolates the attack surface inside a private virtual network, routing traffic safely away from your host machine.

* **Attacker Node:** Kali Linux (Reconnaissance & Exploitation)
* **Defense & SIEM:** Wazuh Manager (Centralized Log Analytics & Alerting Dashboard)
* **Network IDS/IPS:** Snort (Signature-based Network Intrusion Detection)
* **Target Endpoints:** Windows Server & Linux Metasploitable instances (Running Wazuh Agents)

---

## 🛠️ Tech Stack

* **Hypervisor:** VirtualBox / VMware Workstation
* **SIEM & Endpoint Detection:** Wazuh (v4.x)
* **Network Monitoring:** Snort NIDS
* **Offensive Tools:** Nmap, Metasploit Framework, Hydra
* **OS Platforms:** Kali Linux, Ubuntu Server (SIEM host), Windows 10/Server

---

## 🌟 Key Features

* **Real-Time Threat Detection:** Configured custom Snort rules to detect network anomalies, stealthy port scans, and signature-based malicious traffic.
* **Centralized Log Management:** Deployed a Wazuh SIEM to aggregate security events, monitor endpoint file integrity (FIM), and track system event logs.
* **Attack Simulation & Verification:** Executed controlled network reconnaissance, brute-force attacks, and exploit delivery using Kali Linux to validate rule triggers and alerting mechanisms.
* **Automated Alerting:** Designed custom Kibana/Wazuh detection dashboards to visualize attack surfaces and prioritize critical security incidents.

---

## 🚀 Setup & Installation

### Prerequisites
* Minimum **16GB RAM** recommended on the host machine.
* VirtualBox or VMware installed.

### Step 1: Network Configuration
1. Create a **Host-Only Network** or a isolated **NAT Network** within your hypervisor (e.g., Subnet `192.168.56.0/24`).
2. Ensure all virtual machines are attached to this network interface to allow internal communication while isolating them from your home network.

### Step 2: SIEM & Agent Deployment
1. Deploy an Ubuntu Server instance and install the **Wazuh Manager** using the quick-start installation script:
```bash
   curl -sO [https://packages.wazuh.com/4.x/wazuh-install.sh](https://packages.wazuh.com/4.x/wazuh-install.sh) && sudo bash wazuh-install.sh -a
