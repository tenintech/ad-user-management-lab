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

Drive appears
Access works
Outcome

Shared company drive deployed using Group Policy.
