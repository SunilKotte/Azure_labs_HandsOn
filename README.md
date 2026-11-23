# ☁️ Microsoft Azure Hands-On Cloud & Networking Labs

A collection of hands-on infrastructure labs demonstrating cloud networking, Linux server administration, stateful firewall security, and high-availability traffic routing in Microsoft Azure.

---

## 📂 Lab Projects Overview

### 1. [High-Availability Web Architecture with Azure Load Balancer](./screenshots/LoadBalncer_Lab(LB_VMs_Vnets_NSGs_HealthProbes_LBRules)/README.md)
* **Core Services:** Azure Standard Load Balancer, Virtual Networks (VNets), Linux Virtual Machines, Network Security Groups (NSGs), Health Probes, Load Balancing Rules.
* **What I Built:** Deployed a multi-VM web tier behind an Azure Standard Load Balancer to distribute incoming HTTP traffic across healthy backend instances.
* **Key Project Learnings:**
  * **Layer 4 Traffic Distribution:** Configured frontend IP configurations, backend pools, and load balancing rules to route TCP/HTTP requests across multiple VMs.
  * **Automated Failover & Health Monitoring:** Implemented custom health probes to continuously monitor instance availability and automatically remove unhealthy nodes from rotation.
  * **End-to-End Traffic Validation:** Verified load distribution and session behavior both via browser refreshes and CLI/terminal requests.

---

### 2. [Securing & Deploying a Web Server using Network Security Groups (NSGs)](./screenshots/Securing_&_Deploying_WebServer_using_Network_Security_Groups_(NSGs)/README.md) 
* **Core Services:** Azure Virtual Machines (Ubuntu Linux), Virtual Networks (VNets), Network Security Groups (NSGs), SSH, Apache2.
* **What I Built:** Provisioned an Ubuntu web server in Azure, locked down inbound network access using stateful NSG rules, and deployed Apache2 over HTTP.
* **Key Project Learnings:**
  * **Principle of Least Privilege (PoLP):** Replaced Azure's default `DenyAllInBound` posture with granular, priority-ordered allow rules strictly for SSH (Port 22) and HTTP (Port 80).
  * **Stateful Firewall Behavior:** Observed how NSGs evaluate inbound security rules and automatically permit return outbound traffic for established sessions.
  * **Network Layer Troubleshooting:** Isolated service-level availability (`systemctl status apache2`) from network-level packet drops when diagnosing connection timeouts.

---

## 🛠️ Core Technical Skills Demonstrated
* **Cloud Networking:** VNets, Subnets, Public/Private IPs, Standard Load Balancers, Health Probes, NSG Rule Priorities
* **Security & Hardening:** Stateful Firewalls, SSH Key-Pair Authentication, Least-Privilege Port Exposure
* **Linux & Operations:** Ubuntu Server Administration, Apache2 Web Server Deployment, CLI Connectivity Testing (`ssh`, `curl`)