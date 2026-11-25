# ☁️ Microsoft Azure Hands-On Cloud & Networking Labs

A collection of hands-on infrastructure labs demonstrating cloud networking, Linux server administration, stateful firewall security, and high-availability traffic routing in Microsoft Azure.

---

## 📂 Lab Projects Overview

### 1. [High-Availability Web Architecture with Azure Load Balancer](./HandsOn_Projects/LoadBalncer_Lab(LB_VMs_Vnets_NSGs_HealthProbes_LBRules)/README.md)
* **Core Services:** Azure Standard Load Balancer, Virtual Networks (VNets), Linux Virtual Machines, Network Security Groups (NSGs), Health Probes, Load Balancing Rules.
* **What I Built:** Deployed a multi-VM web tier behind an Azure Standard Load Balancer to distribute incoming HTTP traffic across healthy backend instances.
* **Key Project Learnings:**
  * **Layer 4 Traffic Distribution:** Configured frontend IP configurations, backend pools, and load balancing rules to route TCP/HTTP requests across multiple VMs.
  * **Automated Failover & Health Monitoring:** Implemented custom health probes to continuously monitor instance availability and automatically remove unhealthy nodes from rotation.
  * **End-to-End Traffic Validation:** Verified load distribution and session behavior both via browser refreshes and CLI/terminal requests.

---

### 2. [Securing & Deploying a Web Server using Network Security Groups (NSGs)](./HandsOn_Projects/Securing_&_Deploying_WebServer_using_Network_Security_Groups_(NSGs)/README.md) 
* **Core Services:** Azure Virtual Machines (Ubuntu Linux), Virtual Networks (VNets), Network Security Groups (NSGs), SSH, Apache2.
* **What I Built:** Provisioned an Ubuntu web server in Azure, locked down inbound network access using stateful NSG rules, and deployed Apache2 over HTTP.
* **Key Project Learnings:**
  * **Principle of Least Privilege (PoLP):** Replaced Azure's default `DenyAllInBound` posture with granular, priority-ordered allow rules strictly for SSH (Port 22) and HTTP (Port 80).
  * **Stateful Firewall Behavior:** Observed how NSGs evaluate inbound security rules and automatically permit return outbound traffic for established sessions.
  * **Network Layer Troubleshooting:** Isolated service-level availability (`systemctl status apache2`) from network-level packet drops when diagnosing connection timeouts.

---

### 3. [Azure Functions (Python) — Timer Trigger Deployment & Troubleshooting](./HandsOn_Projects/Azure_func_App/readme.md)
- *Core Services:* Azure Functions (Linux Consumption Plan, Python 3.11), Azure Storage Account (`Standard_LRS`, `StorageV2`), CRON Timer Trigger (`*/5 * * * * *`), Azure CLI (`az`), Azure Functions Core Tools (`func` v4), Oryx Remote Build.
- *What I Built:* Deployed a serverless Python v2 Timer Trigger function (`timerTriggerAppFunc01`) in `eastus2` via Azure CLI and Core Tools, along with a root-cause troubleshooting guide for Windows PowerShell deployment and runtime build issues.
- *Key Project Learnings:*
  - *Windows PowerShell CLI Parsing:* Used PowerShell's stop-parsing token (`--%`) when setting `--linux-fx-version "Python|3.11"` so `cmd.exe` does not misinterpret the pipe (`|`) character as a command pipeline operator.
  - *Kudu/SCM Initialization & 503 Recovery:* Resolved `503 (Site Unavailable)` deployment errors after provisioning by verifying Storage Account network access (`defaultAction: "Allow"`), explicitly setting `FUNCTIONS_WORKER_RUNTIME=python` and `linuxFxVersion`, and restarting the app to let the background Kudu/SCM container stabilize.
  - *Runtime Version Alignment via Oryx:* Prevented dependency incompatibilities between local Python `3.15.2` and Azure's supported `3.9–3.13` runtimes by deploying with `--build remote` so Microsoft Oryx compiles `requirements.txt` inside the target Linux Python 3.11 container.


---

## 🛠️ Core Technical Skills Demonstrated
- **Networking & Traffic Management:** Azure Virtual Networks (VNets), Subnets, Network Security Groups (NSGs), Azure Load Balancer (Standard SKU), Health Probes, Load Balancing Rules, Public/Private IP Addressing.
- **Compute & Serverless Architecture:** Azure Virtual Machines (Ubuntu Linux), Azure Functions (Python v2 Programming Model, Linux Consumption Plan), CRON Timer Triggers (`NCRONTAB`), Oryx Remote Build.
- **Storage & Runtime Management:** Azure Storage Accounts (`Standard_LRS`, `StorageV2`), Host Storage Configuration (`AzureWebJobsStorage`), Python Runtime & Dependency Isolation.
- **CLI Automation & Diagnostics:** Azure CLI (`az`), Azure Functions Core Tools (`func` v4), PowerShell Argument Escaping (`--%`), Kudu/SCM Deployment Diagnostics, Live Log Streaming (`logstream`), SSH, Apache Web Server.