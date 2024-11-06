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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<h2>Creating Users with PowerShell</h2>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
