<h1>Group Policy & Shared Drive Lab</h1>

  Objective

Deploy shared resources and company policies using Group Policy.

Technologies / Environments Used
Active Directory
Group Policy Management
Windows Server File Share
Domain client
Lab Steps
Step 1 — Create Shared Folder

On the server create:

CompanyShare

Share path:

\\DC01\CompanyShare
Step 2 — Configure Permissions

Grant access to:

Domain Users
Specific groups
Step 3 — Create Group Policy

Open Group Policy Management.

Create new policy:

Map Network Drive
Step 4 — Map Network Drive

Navigate to:
User Configuration → Preferences → Drive Maps

Configure:
Drive letter:

Z:
Step 5 — Test Policy

Login to a domain client and confirm:


Step 2 — Install Active Directory


 1. Open Server Manager.

 2. Click Add Roles and Features.
      Select:
         - Active Directory Domain Services.

 3. Complete the installation.




   
<b>Step 3 — Promote Server to Domain Controller<b>

1. Click Promote this server to a domain controller.

2. Select:
     - Create a new forest.

3. Name Domain (Domain name example):

       company.local
4. Complete the configuration and restart.


<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
![Alt text](https://github.com/tenintech/ad-infrastructure/blob/25347f832d878dc31009e41f8f6787fd66c7d5d2/2created%20dc.png)
 <img src=""C:\Users\Teni\OneDrive\Pictures\Capturas de pantalla\1.Prepare AD Infrastructure\1resource group.png"" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="[https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps](https://github.com/tenintech/ad-infrastructure/blob/main/1resource%20group.png?raw=true)"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

![Image Alt](image_url)


Drive appears
Access works
Outcome

Shared company drive deployed using Group Policy.
