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
- 
Add user to _ADMINS OU 
User Name: Jane Doe 

Make User an Admin user adding user to built in admin security group "Domain Admins"
<img width="1113" height="372" alt="11adding user to built in domain admins sec group" src="https://github.com/user-attachments/assets/c1bccb9e-b9bd-4f68-8ded-3dc9e9493fb6" />

<img width="1289" height="869" alt="10 create user in ADUC" src="https://github.com/user-attachments/assets/5351520b-bf57-45c0-ae62-f10dc6929f5b" />


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

Example user:
- bot.vug


Verify the users appear in the OU.

<img width="1755" height="908" alt="17using powershell to create users" src="https://github.com/user-attachments/assets/9a7056c1-c6d2-49f1-ad24-1b585755578a" />

<hr />

<br />

<h3>6. Configure Basic Group Policy</h3>

Open Group Policy Management.

Create a new Group Policy Object (GPO) to apply basic domain settings.

Example configuration:
- Password policy
- Account lockout policy
- Desktop restrictions

Link the policy to the appropriate Organizational Unit.

Verify the policy applies to domain users.

<img width="1223" height="834" alt="19using GPMC to create GPO for Password Threshold" src="https://github.com/user-attachments/assets/d99b1fe3-fadc-4506-8a83-f57fc6c54e9b" />

After setting the password threshold I attempted to login as user "bot.vug" with the wrong password 10 times and was locked out of the account. 
Unlock the account
Reset the password


<img width="1235" height="902" alt="23Unlocking user account" src="https://github.com/user-attachments/assets/2ac6be79-4175-45c7-a1d2-8642f4e9a1d0" />

<h4>Apply a Desktop Restriction Policy</h4>

To simulate a managed work environment, a desktop restriction policy was created to prevent standard users from accessing the Control Panel and system settings.

Steps:
- Open Group Policy Management
- Edit the existing Group Policy Object
- Navigate to:

User Configuration → Administrative Templates → Control Panel

Enable the policy:
Prohibit access to Control Panel and PC settings

Apply the policy to the _EMPLOYEES Organizational Unit.

<img src="ADD CONTROL PANEL GPO SCREENSHOT HERE">

Test the policy:
- Log into Client1 as a standard user
- Attempt to open Control Panel

Result:
Access to Control Panel is restricted by the Group Policy.

## What I Learned
Once the server is promoted to a Domain Controller, it changes how users authenticate within the environment. Now users can sign on and be local users, or sign on as domain users. It becomes necessary when you log in to specify how you want to interact with the domain. 

<h2>⏭️Next Steps</h2>

In the next phase of this lab I'll:
- Implement Group Policy Objects (GPO)
- Create additional users in the _EMPLOYEES OU
- Test domain logins from Client1
- Configure password policies
- Simulate help desk tasks such as password resets and account unlocks
