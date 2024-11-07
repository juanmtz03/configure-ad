<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 

<h2>High-Level Deployment and Configuration Steps</h2>

- Active Directory Architecture Overview
- Preparing AD Infrastructure in Azure
- Deploying Active Directory
- Creating Users with PowerShell

<h2>Active Directory Architecture Overview</h2>

<p align="center">
<img width="400" alt="image" src="https://github.com/user-attachments/assets/5169b265-7d96-4e92-b80f-6ef8e6f87d62">
</p>

<br />

<h2>Preparing AD Infrastructure in Azure</h2>
<div align="center" style="display: grid; grid-template-columns: 4fr 1fr; gap: 5px; width: 80%; max-width: 400px;">
    <img src="https://github.com/user-attachments/assets/5d952fde-9cdf-4810-a012-87161c20b880" alt="image" style="width: 50%; height: auto;">
    <img src="https://github.com/user-attachments/assets/be1e09b1-3cf6-44e1-81cd-a1067a99cd2f" alt="image" style="width: 50%; height: auto;">
    <img src="https://github.com/user-attachments/assets/6805cd05-8ca7-4b09-b508-209b33ed8bbe" alt="image" style="width: 50%; height: auto;">
    <img src="https://github.com/user-attachments/assets/1c184c13-2f29-4504-8916-d060c4b4e4ad" alt="image" style="width: 50%; height: auto;">
</div>
<p>
To set up a domain controller in Azure, first create a resource group, then establish a virtual network and subnet. Deploy a virtual machine (VM) for the domain controller, naming it “DC-1” and using Windows Server 2022 with the login credentials “labuser” and “lab123!”. After creating the VM, set its NIC’s private IP address to static and disable the Windows Firewall for testing. For the client setup, create a second VM, “Client-1,” with Windows 10 and the same credentials, placing it in the same region and virtual network as DC-1. Update Client-1’s DNS settings to match DC-1’s private IP, restart it from the Azure Portal, and then confirm connectivity by pinging DC-1’s IP. Lastly, verify through PowerShell on Client-1 that DC-1’s private IP is set as its DNS server.
</p>
<br />


<h2>Deploying Active Directory</h2>
<p>
To set up Active Directory, first, log into the primary domain controller (DC-1) and install Active Directory Domain Services. Then, promote DC-1 to a domain controller by creating a new forest (e.g., mydomain.com) and logging back in with the designated domain user. Next, create a Domain Admin user in Active Directory Users and Computers (ADUC). Establish Organizational Units (OUs) for both employees and admins, then create an admin user, “jane_admin,” with assigned permissions. Log in as jane_admin for ongoing administrative tasks. Finally, connect Client-1 to the domain by configuring its DNS settings in Azure, joining it to the domain, and organizing it under a designated “_CLIENTS” OU. When the lab is finished, keep the virtual machines for future work, but turn them off in the Azure Portal to save costs.
</p>

Key Steps for Setting up Active Directory in Lab

- **Install Active Directory Domain Services**
  - Log into `DC-1`, install the service, and promote it to a domain controller.
  - Set up a forest (e.g., `mydomain.com`), then restart.

- **Create Domain Admin User**
  - In `Active Directory Users and Computers (ADUC)`, create an `_EMPLOYEES` and an `_ADMINS` Organizational Unit (OU).
  - Create a new user `jane_admin` in the `_ADMINS` OU with the username `jane_admin` and password `Cyberlab123!`.
  - Add `jane_admin` to the `Domain Admins` Security Group.
  - Use `jane_admin` as the admin account for all future administrative tasks.

- **Join Client-1 to Domain**
  - Set `Client-1`’s DNS in Azure to the DC’s private IP address.
  - Restart `Client-1` and join it to the domain as the local admin `labuser`.
  - Verify that `Client-1` appears in `ADUC`, then move it to the `_CLIENTS` OU.

<br/>

<h2>Creating Users with PowerShell</h2>

<p>
Setting Up Remote Desktop for Non-Administrative Users on Client-1

- **Configure Remote Desktop Access**
  - Log into `Client-1` as `mydomain.com\jane_admin`.
  - Open System Properties.
  - Select “Remote Desktop” and allow access to “domain users.”
  - You can now log into `Client-1` as a normal, non-administrative user.

Create Additional Users and Test Remote Login

- **Create Additional Users with PowerShell**
  - Log into `DC-1` as `jane_admin`.
  - Open `PowerShell_ISE` as an administrator.
  - Create a new file (send me an email for the code 'juanmtz_3@hot..'), paste the user creation script into it, and run the script.
  - Observe as the accounts are created.

- **Verify Accounts and Test Login**
  - Open `Active Directory Users and Computers (ADUC)` and check the `_EMPLOYEES` OU for the new accounts.
  - Try logging into `Client-1` with one of the new accounts (ensure you know the password set in the script).
</p>
<br />
