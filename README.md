<p align="center">
<img width="300" height="168" alt="Active Directory Img" src="https://github.com/user-attachments/assets/e9927977-2cd2-42b1-8398-85ac11f0b461" />

<h1> Active Directory Deployment and User Management</h1>
This lab is part of my hands-on IT support and cloud infrastructure training portfolio.
<h2>Objective</h2>
This project shows the installation of Active Directory on the Domain Server. It walks through the steps of joining the Virtual Machine to the domain, using Active Directory Users and Computers (ADUC) to create an Organizational Unit, create users and practice log ins.


<h2>Technologies/Environments Used</h2>
  
  - Microsoft Azure(Virtual Machines, Virtual Network)
    
       - Windows Server 2025 (Domain Controller)
 
       - Windows 10 Enterprise Version 22H2 x64 Gen 2 (Client Machine)
  
  - Active Directory Domain Services (AD DS)
  
  - Remote Desktop (RDP)
  
  - PowerShell
  


<br />



<h2>Step-by-Step Walkthrough</h2>

<h3>1. Install Active Directory Domain Services onto the Domain Controller</h3>

Open Server Manager on the Domain Controller and install AD DS.
Promote Server to Domain Controller

Configuration:
- Virtual Machine Name: DC1
- Image: Windows Server 2025
- Virtual Network: Same network that will be used by the client machine

<img width="1567" height="905" alt="1using server manager to add roles and features" src="https://github.com/user-attachments/assets/6488dae0-df73-424a-bb89-20e2e548e887" />
<img width="1361" height="611" alt="2choose server" src="https://github.com/user-attachments/assets/c8863979-0800-491b-84f1-5738eee5efcb" />


<hr />

<br />

<h3>2. Promote Server to a Domain Controller</h3>

Set up a new forest.

Configuration:
- Root domain name: domain.local
- Functional Level of Forest and Domain: Windows Server 2025

<img width="939" height="480" alt="5add new forest" src="https://github.com/user-attachments/assets/a5f020dd-79da-4749-8db1-98cf94249da1" />

<img width="1210" height="809" alt="4promote server to domain controller" src="https://github.com/user-attachments/assets/aaf346b7-e869-4004-974e-3b7dce2bff98" />

<img width="772" height="896" alt="Screenshot 2026-03-23 211626" src="https://github.com/user-attachments/assets/94a7bd43-a2d9-46c1-ae0b-67f3b21fb85d" />

<hr />

<br />

<h3>3. Create a Domain Admin user within the domain</h3>

Open up Active Directory Users and Computers(ADUC) and create 2 Organizational Units (OU)

Create the following Organizational Units (OU):

- _EMPLOYEES
- _ADMINS
  
Add user to _ADMINS OU 
User Name: Jane Doe 
<img width="1289" height="869" alt="10 create user in ADUC" src="https://github.com/user-attachments/assets/5351520b-bf57-45c0-ae62-f10dc6929f5b" />


<br />

Make User an Admin user adding user to built in admin security group "Domain Admins"

<br />
<img width="1113" height="372" alt="11adding user to built in domain admins sec group" src="https://github.com/user-attachments/assets/c1bccb9e-b9bd-4f68-8ded-3dc9e9493fb6" />




<hr />

<br />

<h3>4. Join Client1 to the Domain</h3>

Log into Client1 (VM) and in System Settings make a member of domain.local 
Verify that user is visible in the domain in Computers 


<img width="1920" height="966" alt="12making client1 member of domain" src="https://github.com/user-attachments/assets/0a78a265-70d2-4030-8ea2-824dcef27713" />

<img width="1065" height="561" alt="15client1 computer visible from DC" src="https://github.com/user-attachments/assets/7015fd30-53e5-4659-a3c5-eb301d67b8b0" />

This demonstrates a working Active Directory domain environment with a connected client computer.

<hr />

<br />

<h3>5. Create Additional Domain Users</h3>

Open Active Directory Users and Computers (ADUC).

Navigate to the Organizational Unit:
_EMPLOYEES

Open Powershell and use a script to Create several test users to simulate a real company environment.
Notice path of script.


<img width="1755" height="908" alt="17using powershell to create users" src="https://github.com/user-attachments/assets/56175b86-efa4-474d-833c-112639062b22" />


Example user:
- bot.vug

Logging in as new user: bot.vug


<img width="1920" height="1080" alt="18login as new user" src="https://github.com/user-attachments/assets/62c72f24-1291-4832-90dc-ed435e6e9bf4" />

Verify the users appear in the OU.







<hr />

<br />


## What I Learned
Once the server is promoted to a Domain Controller, it changes how users authenticate within the environment. Now users can sign on and be local users, or sign on as domain users. It becomes necessary when you log in to specify how you want to interact with the domain. 
There are a seemingly infinite amount of things you can enable and disable in Group Policy Management. 

<h2>⏭️Next Steps</h2>

In the next phase of this lab I'll:
- Implement Group Policy Objects (GPO)
- Create additional users in the _EMPLOYEES OU
- Test domain logins from Client1
- Configure password policies
- Simulate help desk tasks such as password resets and account unlocks
