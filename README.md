# Azure SOC - Assembling a SOC & Honeynet in Azure
<br /> <br />
![image](https://github.com/user-attachments/assets/2bcf8f52-9c68-460b-869b-02248ed3f998)


## Introduction

In this project, I used Microsoft Azure to build a honeynet where I ingest log sources from various resources into a Log Analytics workspace. The Log Analytics workspace was used by Microsoft Sentinel to build attack maps, trigger alerts, and create incidents, giving me hands on experience with a SIEM. The cloud-natice platform allowed me to measure security metrics in the insecure environment for 24 hours, apply some security controls to harden the environment, measure metrics for another 24 hours, then show the results below. The metrics shown in the project are the following:

- SecurityEvent (Windows Event Logs)
- Syslog (Linux Event Logs)
- SecurityAlert (Log Analytics Alerts Triggered)
- SecurityIncident (Incidents created by Sentinel)
- AzureNetworkAnalytics_CL (Malicious Flows allowed into the Honeynet)
<br /> <br />
## Environment Setup
To start off with this project, I created an Azure subscription and used the resources avliable in Azure to provision VMs. I experimented with different resources, such as Microsoft Entra ID, before proceeding with the Log Analytics workspace setup. After connecting the VMs to the log analytics workspace, I also connected a key vault, a blob storage, and Sentinel. Under Sentinel's workbooks, I included attack maps to show the locations of potential attackers. Everything was all centralized around the Log Analytics workspace.
<br /> <br />
## Environment Before Hardening / Security Controls
Several security incidents occured due to the environment being left open to malicious actors. The arcitecture was connected to Microsoft Sentinel via the Log Analytics workspace which allowed for these incdents to be triggered. A majority of the incidents triggered were from brute force attacks by threat actors from around the world.
<br /> <br />
![image](https://github.com/user-attachments/assets/5b84884f-e93a-47fb-a698-ba06ba181e6c)


## Environment After Hardening / Security Controls
![image](https://github.com/user-attachments/assets/6d68a5ca-1c87-4e3b-804b-627692488aa3)

<br /> <br />
The architecture of the mini honeynet in Azure consists of the following components:

- Virtual Network (VNet)
- Network Security Group (NSG)
- Virtual Machines (2 windows, 1 linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel
<br /> <br />
For the before metrics, all resources were originally created with weak security intentionally and exposed to the internet. The Virtual Machines had both their Network Security Groups and built-in firewalls wide open, and all other resources are deployed with public endpoints visible to the Internet.
<br /> <br />
For the "AFTER" metrics, Network Security Groups were hardened by blocking ALL traffic with the exception of my admin workstation, and all other resources were protected by their built-in firewalls as well as Private Endpoint
<br /> <br />
## Attack Maps Before Hardening / Security Controls
![image](https://github.com/user-attachments/assets/7975396a-253b-495f-9755-bef1a1269c83)
<br>
![image](https://github.com/user-attachments/assets/a0703fa1-2d52-4cd1-a909-795931541535)
<br>
![image](https://github.com/user-attachments/assets/15e99095-2b13-4995-a74c-e88ce13d30a9)
<br>
<br /> <br />
## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
<br /> <br />
Start Time 2024-09-18 14:17    
Stop Time 2024-09-19 14:19
<br /> <br />

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 63647
| Syslog                   | 4945
| SecurityAlert            | 10
| SecurityIncident         | 152
| AzureNetworkAnalytics_CL | 2170

<br /> <br />
## Attack Maps After Hardening / Security Controls

All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.
<br /> <br />
## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
<br /> <br />
Start Time 2024-09-19 15:34    
Stop Time 2024-09-20 15:34
<br /> <br />

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 24278
| Syslog                   | 0
| SecurityAlert            | 0
| SecurityIncident         | 0
| AzureNetworkAnalytics_CL | 0

<br /> <br />
## Conclusion

In this project, I set up a honeynet in Microsoft Azure and log sources were integrated into the Log Analytics workspace created for this project. Microsoft Sentinel was used to trigger alerts and create incidents based on the ingested logs. Also, metrics were measured in the insecure environment before security controls were applied and after implementing security measures. The number of security events and incidents were greatly reduced after the security controls were applied, demonstrating their effectiveness.
<br /> <br />
After completing this project, I have a better understanding of how Microsoft Azure azure works, and I have deepened my understanding of SIEM tools and log aggregation. I also learned how to use KQL to query different metrics. The project served as a valuable experience that I intend to build upon in the near future.
