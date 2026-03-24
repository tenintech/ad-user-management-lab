
<img width="300" height="168" alt="Active Directory Img" src="https://github.com/user-attachments/assets/e9927977-2cd2-42b1-8398-85ac11f0b461" />

<h1> Active Directory Deployment and User Management</h1>
<h2>Objective</h2>
This project shows the installation of Active Directory on the Domain Server. It walks through the steps of joining the Virtual Machine to the domain, using Active Directory Uses and Computers (ADUC) to create an Organizatinal Unit, create users and practice log ins.


<h2>Technologies/Environments Used</h2>
  
  - Microsoft Azure(Virtual Machines, Vitual Network)
    
       - Windows Server 2025 (Domain Controller)
 
       - Windows 10 Enterprise Version 22H2 x64 Gen 2 (Client Machine)
  
  - Active Directory Domain Services (AD DS)
  
  - Remote Desktop (RDP)
  
  - PowerShell
  


<br />



<h2>Step-by-Step Walkthrough</h2>

<h3>1. Install Active Directory Domain Services onto the Domain Controller</h3>

Open Server Manager on the Domain Contoller and install AD DS.
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

Create: 
Organization Units: _EMPLOYEES 
                    _ADMINS
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

This show A working Active Directory domain environment with a connected client computer.

<hr />

<br />

<h3>5. Configure Client DNS Settings</h3>

Set the DNS server of the client virtual machine (Client1) to point to the private IP address of the Domain Controller (DC1).

This allows the client machine to locate and authenticate with the domain once Active Directory is installed.

<img width="1076" height="996" alt="Changing DNS Settings on Client VM" src="https://github.com/user-attachments/assets/64087d13-0377-48f8-8104-4e5e3fd8c581" />

<hr />

<br />

<h3>6. Test Network Connectivity</h3>

Open PowerShell on Client1 and test connectivity to the Domain Controller using the ping command.

Use:
ping 10.0.0.4

Then verify DNS configuration using:
ipconfig /all

This confirms that the client machine is using the Domain Controller as its DNS server.

<img width="951" height="967" alt="Successful Ping Test" src="https://github.com/user-attachments/assets/e72a658e-4c85-41d4-ab91-57dc85b4d0e8" />

<img width="1080" height="925" alt="DNS Configuration Confirmation" src="https://github.com/user-attachments/assets/80e8d3d8-04b1-43d2-91d9-876d1890156b" />

<hr />

## What I Learned
During this lab I learned how important DNS configuration is when setting up Active Directory in Azure. This is necessary so that the users computers don't go looking out on the world wide web but get their information from inside the domain. 

<h2>⏭️Next Steps</h2>

In the next phase of this lab I'll:
- Install Active Directory Domain Services (AD DS)
- Promote the server to a Domain Controller
- Join Client1 to the domain
- Create test user accounts
