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

<h2>Deploying Active Directory ann create Admin Account<h2>

<p>
<img width="1373" alt="Screenshot 2024-09-10 at 2 22 45 PM" src="https://github.com/user-attachments/assets/54b28230-526f-4769-b828-e99914f5a87d">
<img width="1373" alt="Screenshot 2024-09-10 at 2 23 43 PM" src="https://github.com/user-attachments/assets/f0fb9c45-34e5-4d47-950e-ec59adbdc2a1">
<img width="1373" alt="Screenshot 2024-09-10 at 2 23 59 PM" src="https://github.com/user-attachments/assets/b2dc8faa-b0d0-4c24-8647-bfd896212caf">
<img width="1373" alt="Screenshot 2024-09-10 at 2 24 08 PM" src="https://github.com/user-attachments/assets/7960143d-49ee-4930-8b73-9e34757acde0">
<img width="1373" alt="Screenshot 2024-09-10 at 2 24 52 PM" src="https://github.com/user-attachments/assets/a1f0da93-9c17-4ff5-aa0e-20ce4e8a62ae">
<img width="1373" alt="Screenshot 2024-09-10 at 2 25 11 PM" src="https://github.com/user-attachments/assets/5b88de35-bdcb-4a76-98ce-3329156faab4">
<img width="1373" alt="Screenshot 2024-09-10 at 2 27 01 PM" src="https://github.com/user-attachments/assets/0012a84b-9768-475e-89f2-0a24c3474a88">
<img width="1373" alt="Screenshot 2024-09-10 at 2 28 09 PM" src="https://github.com/user-attachments/assets/0e0957f7-88f6-4357-b845-487428666cee">
<img width="1373" alt="Screenshot 2024-09-10 at 2 28 38 PM" src="https://github.com/user-attachments/assets/51a8f391-a44c-428f-84f0-a1e617c600d7">
<img width="1373" alt="Screenshot 2024-09-10 at 2 31 08 PM" src="https://github.com/user-attachments/assets/825ed699-4669-414d-ab55-0945c57b3410">
<img width="1373" alt="Screenshot 2024-09-10 at 2 31 23 PM" src="https://github.com/user-attachments/assets/1473197c-81ba-448b-9f7f-c7ed9927b00a">
<img width="1373" alt="Screenshot 2024-09-10 at 2 32 20 PM" src="https://github.com/user-attachments/assets/cca60807-62a0-425d-ac47-4dfe3be0d5b4">
<img width="1373" alt="Screenshot 2024-09-10 at 2 32 53 PM" src="https://github.com/user-attachments/assets/d0eb7587-eba7-4df4-bee4-a7cf5f12ce0e">
<img width="1373" alt="Screenshot 2024-09-10 at 2 33 48 PM" src="https://github.com/user-attachments/assets/15ef6337-7520-4659-beb7-de2defcef989">
<img width="1373" alt="Screenshot 2024-09-10 at 2 34 20 PM" src="https://github.com/user-attachments/assets/aabd415f-5c51-4fd2-9a40-539b35c8d559">
  <img width="1225" alt="Screenshot 2024-09-10 at 2 36 39 PM" src="https://github.com/user-attachments/assets/09bb0b10-39ff-469a-92f6-8d20b4d652af">
<img width="1225" alt="Screenshot 2024-09-10 at 2 36 57 PM" src="https://github.com/user-attachments/assets/65dd3a05-d88b-4d49-a51c-01b1bac77123">
<img width="1225" alt="Screenshot 2024-09-10 at 2 37 18 PM" src="https://github.com/user-attachments/assets/dd05d787-8dd3-42a1-80d1-ac6ae0558c16">
<img width="1225" alt="Screenshot 2024-09-10 at 2 38 01 PM" src="https://github.com/user-attachments/assets/1dff4a51-3609-46ed-92cf-64c2fece23bd">
</p>
<p>
Now that Vms are extablished we are going to install active directory domain services and promote DC-1 as an actual DC"im going to setup a new forest as mydomain.com" then restart DC-1. now that its a actual DC the username to get into DC-1 vm is now mydomain.com\labuser"password still the same"and now that ACTIVE DIRECTORY is installed we are going to add a domain admin user with the domain.Going to Active directory users and computers create an organzation unit name emplyees and one name admins now we are going to create an admin(JANE DOE WILL BE MY DOMAIN ADMIN) username will be Jane_admin with a password of choosing.But because jane_admin is added to admins folder its not yet an admin untill we add jane_admin to SECURITY GROUPS,then after that log out of DC-1 AND Log backin as mydomain.com\jane_admin, and that will be our new admin account.Now login to Client-1 vm with original credintals and join it to the domain vm will restart,and after that log into DC-1 and verify Client-1 shows up in computers and Create a new Organization unit file and name it _Clients and drag Clinet-1 into there.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
