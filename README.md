# 🔍 Splunk Enterprise Log Collection Lab

This lab demonstrates the full setup and configuration of **Splunk Enterprise** to collect and analyze Windows event logs in a simulated domain environment. The goal was to create a centralized log monitoring solution for multiple domain devices using a Universal Forwarder and Splunk's web interface.

## 🧠 Lab Objectives

- Install and configure **Splunk Enterprise**
- Enable TCP data input on port `9997`
- Configure **Windows Firewall** to allow Splunk traffic
- Install and configure **Splunk Universal Forwarder** on a domain member server
- Forward logs from ACIDM01 to ACIWIN11
- Collect and search Windows **Application**, **Security**, and **System** event logs

---

## 🖥️ Environment Setup

| Device Name | OS                  | Role                      |
|-------------|---------------------|---------------------------|
| ACIWIN11    | Windows 11          | Domain Member Workstation            |
| ACIDM01     | Windows Server 2022 | Domain Member Server    |
| ACIDC01     | Windows Server 2022 | Domain Controller         |

---

## 📦 Tools Used

- **Splunk Enterprise 9.0.3**
- **Splunk Universal Forwarder 9.0.3**
- Windows Defender Firewall
- Microsoft Edge

---

## 🛠️ Key Configurations

### 🔹 Splunk Enterprise Configuration (ACIWIN11)

- Enabled TCP data input on port `9997`
- Firewall rule created to allow inbound traffic on ports `8089`, `9997`
- Created a new Server Class for ACIDM01
- Selected and indexed Application, Security, and System logs

![Port Config](./splunklogcollect1.png)
![Firewall Rules](./splunklogcollect2.png)
![Inbound Rule Added](./splunklogcollect3.png)

---

### 🔹 Splunk Forwarder Setup (ACIDM01)

- Installed Splunk Universal Forwarder with domain credentials
- Forwarded logs to `192.168.0.3` on ports `8089` and `9997`
- Selected Windows Event Log sources

![Select Forwarder](./splunklogcollect4.png)
![Event Log Source](./splunklogcollect5.png)
![Review Config](./splunklogcollect6.png)
![Log Search Results](./splunklogcollect7.png)

---

## 📊 Results

Successfully collected and visualized over **25,000 events** from ACIDM01. Events from all three categories (Application, Security, System) were searchable in Splunk Web.

---

## ✍️ Lessons Learned

- Importance of firewall rules when working with agent-based log forwarding
- How Splunk uses server classes and forwarders to handle input data
- How to parse and analyze Windows Event logs using Splunk Search

---

## 📁 Folder Structure

