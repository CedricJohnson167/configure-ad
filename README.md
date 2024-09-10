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
<img width="1373" alt="Screenshot 2024-09-10 at 11 22 23 AM" src="https://github.com/user-attachments/assets/4edf052a-e96b-40cd-9756-83faf275c22a">
<img width="1373" alt="Screenshot 2024-09-10 at 11 25 18 AM" src="https://github.com/user-attachments/assets/694cbfbf-dca9-4c0b-8cfb-97962423758c">
<img width="1373" alt="Screenshot 2024-09-10 at 11 26 48 AM" src="https://github.com/user-attachments/assets/3a7b013b-fe72-4f2b-9eb7-e6d117173f2d">
<img width="1373" alt="Screenshot 2024-09-10 at 11 27 43 AM" src="https://github.com/user-attachments/assets/e83f5bb6-7198-420b-bb1b-26a1757de150">
<img width="1373" alt="Screenshot 2024-09-10 at 11 27 58 AM" src="https://github.com/user-attachments/assets/0afde7d7-5d2d-4e27-b0f5-cd847d4c021c">
<img width="1373" alt="Screenshot 2024-09-10 at 11 28 33 AM" src="https://github.com/user-attachments/assets/838a5fdf-b6a9-49c3-b720-9ab367f02b41">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 02 AM" src="https://github.com/user-attachments/assets/21566836-2d9c-4d87-aeda-2905bb0f55de">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 16 AM" src="https://github.com/user-attachments/assets/d235ea0e-feeb-48f3-98a2-76a1227c2ea0">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 34 AM" src="https://github.com/user-attachments/assets/b428fd99-ab91-430c-acd2-a97f1ff0ccc0">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 57 AM" src="https://github.com/user-attachments/assets/bbec08a7-5af1-42dd-aafb-da7f22f46efc">
<img width="1373" alt="Screenshot 2024-09-10 at 11 31 20 AM" src="https://github.com/user-attachments/assets/77661518-7c30-45fc-94b6-328ea738ae34">
<img width="1373" alt="Screenshot 2024-09-10 at 11 31 56 AM" src="https://github.com/user-attachments/assets/46db1c22-b038-46dd-84e6-3b296b489e10">
  <img width="1373" alt="Screenshot 2024-09-10 at 11 32 01 AM" src="https://github.com/user-attachments/assets/ff251771-fc51-4f73-9d4d-7736548346ea">
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
