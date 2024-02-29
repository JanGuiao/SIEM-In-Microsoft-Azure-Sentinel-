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

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/425106e1-6e03-4e78-b415-0a935692afd1)

- Skip all except Networking and Monitoring

  ![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/3465f867-d4f6-4055-9945-cf4a8ab92145)

  ![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/85cd0e4f-133d-469e-9fd4-25810c3c81b8)
  
  ![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/8d050c3f-2a4a-44ac-84a8-0adbdd9797a0)






## Create Log Analytics Workspace

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/a232d3b3-113b-47d0-8716-b3b36d446360)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/4afed12d-6b37-458b-a4de-db16073a9b32)




## Enabling VM log gathering in Microsoft Defender for Cloud

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/d7a46623-07ad-4784-b6fc-57329c501d54)





## Connect Log Analytics to VM to "ALL"

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/33f3a4c3-400c-4759-93b4-f6bc62b36edf)





## Setup Azure Sentinel


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/363bb198-9bd1-41a4-b7d9-c505cdd87c80)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/2f468548-298f-4528-8fa9-87a8715c4575)



##  Log into VM with Remote Desktop (failed logons)

On your Default Desktop open Remote Desktop Connection and connect via IP | Username & Password *fail a logon attempt at least once for Event Viewer to capture failed logon entry*


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/c94c853f-1ec3-43c0-90bc-52380d95d99e)



## Observe Event Viewer Logs in VM

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/e7090635-50f2-4eb4-b42a-f0072db46787)



## Turn off Firewall on VM and ping VM

*Turn off Firewall state in Domain | Private | Public*

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/ab2dc0ed-07b4-49fa-ba7e-ca39c7c41b0a)

*Ping VM

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/a08ef48b-7ca3-45c0-ba48-09d32e31ad55)


## PowerShell Script & Geolocation API Key

*We're going to need the API key for the script"

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/3daec94b-ad4d-4575-90e3-70cddc7721b0)


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/37b2a627-a7e2-48e4-81cf-5347dd6ce724)

- Copy this Script:

  
![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/6f2f0c2e-e2c4-4efc-98a0-472aa29d67c3)


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/5286ef76-7582-437a-aeec-6bc2afa69c15)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/281627d4-ead4-4c57-baf5-1d94857f46f2)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/c1a040f4-b76e-4b77-b5a1-dc73f77d8343)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/90c0fa65-f7ca-4a68-8fa6-912698566326)



## Create custom log in Log Analytics Workspace



![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/079403c8-47c9-43e6-87d1-49bd8a664cfe)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/48121d75-437d-4a1f-9ae3-7c81a51601a4)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/2911a619-53f5-48ad-ba79-58e3e6f7b315)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/e0e34f71-3660-4aab-9d42-4bf69b620f9a)


## View logs and failed entries | security events

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/0b4f0c6b-3e01-48ab-91e4-829b9b7ada98)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/5c0f9742-198b-4961-895d-ef0fa2c1c908)




## Setting up Workbook Map | Editing Logs Query


![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/c42c1173-8615-4db4-9c5c-febc8d3712d8)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/82b92f55-07a8-4fbc-b7e2-7e75c24602ff)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/d79ddd53-c79a-498d-a7bb-958b2877ac08)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/e5bab19d-fe2f-4efc-95f4-a48db2692bb0)



## Configuring Map Settings

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/b7484f25-4eec-4fd9-8775-bb174eaa6217)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/9ca44a13-35ee-40c7-b544-7a2ab4ecd331)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/1be6117e-8f3e-4ee2-ab7c-a8564ba01498)

![image](https://github.com/JanGuiao/SIEM-In-Microsoft-Azure-Sentinel-/assets/95273542/333d82fb-c61e-4c05-91ff-0e94d9d16b33)




##


