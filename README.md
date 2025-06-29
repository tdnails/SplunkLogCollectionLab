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

<p align="center">
Open receiving port 9997 in Splunk: <br/>
<img src="images/splunklogcollect1.png" height="80%" width="80%" alt="Splunk Receiving Port"/>
<br /><br />

Configure Windows Firewall inbound rule: <br/>
<img src="images/splunklogcollect2.png" height="80%" width="80%" alt="Firewall Inbound Rule"/>
<br /><br />

Verify new inbound rule exists: <br/>
<img src="images/splunklogcollect3.png" height="80%" width="80%" alt="Firewall Rule Check"/>
</p>

---

### 🔹 Splunk Forwarder Setup (ACIDM01)

- Installed Splunk Universal Forwarder with domain credentials
- Forwarded logs to `192.168.0.3` on ports `8089` and `9997`
- Selected Windows Event Log sources

<p align="center">
Select the Windows host forwarder: <br/>
<img src="images/splunklogcollect4.png" height="80%" width="80%" alt="Select Host"/>
<br /><br />

Choose Event Log sources: <br/>
<img src="images/splunklogcollect5.png" height="80%" width="80%" alt="Select Event Logs"/>
<br /><br />

Review Splunk data input configuration: <br/>
<img src="images/splunklogcollect6.png" height="80%" width="80%" alt="Review Settings"/>
<br /><br />

View log events in Splunk Search: <br/>
<img src="images/splunklogcollect7.png" height="80%" width="80%" alt="Search Results"/>
</p>


---

## 📊 Results

Successfully collected and visualized over **25,000 events** from ACIDM01. Events from all three categories (Application, Security, System) were searchable in Splunk Web.

---



