# SIEM in Microsoft Azure (Sentinel)
This will be my tutorial of a SIEM within Azure Virtual Machine (Sentinel)

## Utilities 
- Remote Desktop

## Environments 
- Microsoft Azure Sentinel

## Operating Systems 
- Windows 10 Pro (22H2)

## Table of Contents: Deployment and Configuration Steps
- Create Virtual Machine
- Allow all in Firewall
- Create Log Analytics Workspace
- Enabling VM log gathering in Microsoft Defender for Cloud
- Connect Log Analytics to VM to "ALL"
- Setup Azure Sentinel
- Log into VM with Remote Desktop (failed logons)
- Observe Event Viewer Logs in VM
- Turn off Firewall on VM and ping VM
- PowerShell Script & Geolocation API Key
- Run Script and gather Geolocation Data
- Create custom log in Log Analytics Workspace
- View logs and failed entries | security events
- Setting up Workbook Map | Editing Logs Query
- Configuring Map Settings

## Create Virtual Machine

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/684d2ba2-4cb6-4d3f-afcc-238095167823)

- Configure Virtual Machine: <br>
Virtual Machine Name: ex *honeypot-vm* <br>
Region: US East US 2 <br>
Zone: No infrastructure redundancy required <br>
Security: Trusted launch <br>
Image: Windows 10 Pro 22H2 <br>
Size: Standard <br>
Admin: Username | Password <br>


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/425106e1-6e03-4e78-b415-0a935692afd1)

- In the Networking section, create an Advanced **NIC network security group**
Create Network Security Group <br>
Delete default inbound rule and add new <br>
Name: *ex: honeypot* <br>
Source: Any | Source Port: * | Destination: Any | Service: Custom | Destination port ranges: * | Protocol: Any | Action: Allow | Priority: 100 | Name: DANGER_ANY <br>

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/85cd0e4f-133d-469e-9fd4-25810c3c81b8)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/3465f867-d4f6-4055-9945-cf4a8ab92145)


- Disable Boot Diagnostics
  
![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/8d050c3f-2a4a-44ac-84a8-0adbdd9797a0)



## Create Log Analytics Workspace

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/a232d3b3-113b-47d0-8716-b3b36d446360)





![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/4afed12d-6b37-458b-a4de-db16073a9b32)




## Enabling VM log gathering in Microsoft Defender for Cloud

- Microsoft Defender for Cloud
Access Microsoft Defender <br>
Under Environment Settings find your Tenant Root Group with the installed features/resources <br>
- Enable Defender plans for *Foundational CSPM* & *Servers* In CSPM
  

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/d7a46623-07ad-4784-b6fc-57329c501d54)





## Connect Log Analytics to VM to "ALL"

- Set Log Analytics Agent *On* to view *All Events* under LogAnalyticsWorkspace-honeypot

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/33f3a4c3-400c-4759-93b4-f6bc62b36edf)





## Setup Microsoft Sentinel

- Headover to Microsoft Sentinel

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/363bb198-9bd1-41a4-b7d9-c505cdd87c80)

- Create Sentinel via workspace *ex: HoneypotLab*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/2f468548-298f-4528-8fa9-87a8715c4575)



##  Log into VM with Remote Desktop (failed logons)

- On your Default Desktop open Remote Desktop Connection and connect via IP | Username & Password *fail a logon attempt at least once for Event Viewer to capture failed logon entry*


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/c94c853f-1ec3-43c0-90bc-52380d95d99e)

- Login via RDP with credentials (Username & Password) *fail login once for log event viewer purposes*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/bbca54f9-0cb8-410a-b61b-d96be04e547b)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/ed77fa51-03ca-469d-9b98-c5f61e8cff7c)


## Observe Event Viewer Logs in VM

*Shown below is **Event ID 4625** as an Audit Failure attempt to RDP in the Virtual Machine | Source Net Add. provided*
![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/e7090635-50f2-4eb4-b42a-f0072db46787)



## Turn off Firewall on VM and ping VM

- Turn off Firewall state in Domain | Private | Public to create successful connectivity between VM

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/ab2dc0ed-07b4-49fa-ba7e-ca39c7c41b0a)

- Ping VM

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/a08ef48b-7ca3-45c0-ba48-09d32e31ad55)


## PowerShell Script & Geolocation API Key

- Create an account through ipgeolocation.io and retrieve API key in profile settings 

*We're going to need the API key for the script*


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/3daec94b-ad4d-4575-90e3-70cddc7721b0)

- Copy and Paste API Key in $API_KEY Field

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/37b2a627-a7e2-48e4-81cf-5347dd6ce724)

- Script Overview to Run:

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/5286ef76-7582-437a-aeec-6bc2afa69c15)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/281627d4-ead4-4c57-baf5-1d94857f46f2)

- Ran script; pulled my first failed logon attempt

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/17e6288c-393b-4c13-8fe0-08a3779836f0)

*When script is run, failed_rdp log is created in the C:\ProgramData directory*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/c1a040f4-b76e-4b77-b5a1-dc73f77d8343)

*updated version of failed_rdp.log entries*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/90c0fa65-f7ca-4a68-8fa6-912698566326)



## Create custom log in Log Analytics Workspace

- Attach failed_rdp.log from ProgramData directory as the target sample log

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/079403c8-47c9-43e6-87d1-49bd8a664cfe)

*Records inside failed_rdp.log file*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/48121d75-437d-4a1f-9ae3-7c81a51601a4)

*Asking for the type of environment and path the failed_rdp.log file is located*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/2911a619-53f5-48ad-ba79-58e3e6f7b315)

- Name your log *my actual ex: FAILED_RDP_WITH_GEO_CL (CL is automatically attached at the end)*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/e0e34f71-3660-4aab-9d42-4bf69b620f9a)


## View logs and failed entries | security events

- In Microsoft Sentinel, under Logs, we are querying the logs via security events

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/0b4f0c6b-3e01-48ab-91e4-829b9b7ada98)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/fae4122c-45e3-45c1-9643-be6fb274076c)

- SecurityEvent query servers as an Event Viewer in Microsoft Azure as related to the Windows Event Viewer (VM)



## Setting up Workbook Map | Editing Logs Query

- Create new Workbook Query <br>
Remove default widgets <br>

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/82b92f55-07a8-4fbc-b7e2-7e75c24602ff)

- Make sure your workspace is attached

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/d79ddd53-c79a-498d-a7bb-958b2877ac08)

- Configure KQL & Run

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/e5bab19d-fe2f-4efc-95f4-a48db2692bb0)



## Configuring Map Settings

- To visualize the query as a map, change the setting under **Visualization** as *Map*
  
![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/b7484f25-4eec-4fd9-8775-bb174eaa6217)

- Map Settings to show Latitude/Longitude

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/9ca44a13-35ee-40c7-b544-7a2ab4ecd331)

Metric Settings <br>
Metric Label: label <br>
Metric Value: event_count <br> 

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/1be6117e-8f3e-4ee2-ab7c-a8564ba01498)

- Overview of Failed RDP Attempts *not limited to* **India** , **Cambodia** **United States** (my failed attempts)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/333d82fb-c61e-4c05-91ff-0e94d9d16b33)


- Time Elapsed: 5 hours <br>
*Germany joins!* <br>

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/7d119cff-3595-49d8-ac21-0b275b9a9302)




