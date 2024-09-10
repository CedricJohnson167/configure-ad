configure-ad
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
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1 Setup virtual infrastructure within azure using Vms & Vnets and deploy them
- Step Via Vms connect Client vm to Direct controller(ADMIN ACC) Vm via private ip address and deploy Active Directory  
- Step 3 Add Over 2000+ randomly genderated user accounts via Powershell with in Direct Controller(ADMIN ACC)
- Step 4 reset passwords, change password,and via Group policy and management accounts settings apply policy regarding account lockout attempts and login attempts 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Winthin Azure create a resource group for your resouces and have it named "Active-Directory"and have resource group located in your region.Next create a virtual network and subnet, and then go to virtual matchine and create it nameing it DC-1(for domain controller).Make sure the OS is operating as WINDOWS SERVER 2022, and username and password"anything thats good for you to remember" then hit review and create and create.After the vm is created set the network ip address to static and login and disable firewall.Now that the Domain Controller(Admin ACC) is created rinse and repeat for a Client VM with minor differences like, OS will be an Windows 10 system name it client-1 and make sure to attach vm to the same region and Vnet as DC-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
