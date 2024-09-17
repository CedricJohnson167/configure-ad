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
- Step 2 Via Vms connect Client vm to Direct controller(ADMIN ACC) Vm via private ip address and deploy Active Directory  
- Step 3 Add Over 2000+ randomly genderated user accounts via Powershell with in Direct Controller(ADMIN ACC)
- Step 4 reset passwords, change password,and via Group policy and management accounts settings apply policy regarding account lockout attempts and login attempts 

<h2> Step1:Deployment and Configuration Steps</h2>
Create a Resource Group
<img width="1373" alt="Screenshot 2024-09-10 at 11 21 52 AM" src="https://github.com/user-attachments/assets/ccff2828-61c4-44d4-b7a6-3d96600e8bc3">
<img width="1373" alt="Screenshot 2024-09-10 at 11 22 23 AM" src="https://github.com/user-attachments/assets/703bef2b-aef3-4c93-9891-3a55cf7e33f4">
<img width="1373" alt="Screenshot 2024-09-10 at 11 22 41 AM" src="https://github.com/user-attachments/assets/209e89f9-7253-468c-97a5-7797fda46893">
Create a Virtual Network and Subnet
<img width="1373" alt="Screenshot 2024-09-10 at 11 23 43 AM" src="https://github.com/user-attachments/assets/bd54b824-277d-4e07-8899-6913e6a97834">
<img width="1373" alt="Screenshot 2024-09-10 at 11 25 18 AM" src="https://github.com/user-attachments/assets/1393340d-4e15-4465-bc25-74958d2b98e5">

Create the Domain Controller VM (Windows Server 2022) named “DC-1”
<img width="1373" alt="Screenshot 2024-09-10 at 11 26 48 AM" src="https://github.com/user-attachments/assets/19d113f8-5450-4393-b476-f4f59d464f5d">

* Username: labuser
* Password: Cyberlab123!
<img width="1373" alt="Screenshot 2024-09-10 at 11 27 43 AM" src="https://github.com/user-attachments/assets/f03648d5-18c4-4b56-8498-6309bd1b79ec">

After VM is created, set Domain Controller’s NIC Private IP address to be static
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 27 AM" src="https://github.com/user-attachments/assets/626c4fa7-9c0f-43b7-a4c7-313107f3b3d5">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 34 AM" src="https://github.com/user-attachments/assets/6cf789da-0232-4c81-aba0-cd41fd3a88e9">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 43 AM" src="https://github.com/user-attachments/assets/17afdff4-c89b-4dd3-b00a-ab6d6a569c83">
<img width="1373" alt="Screenshot 2024-09-10 at 11 30 57 AM" src="https://github.com/user-attachments/assets/0be5d8e7-0581-47a5-b7b6-13c960fa50c9">

Log into the VM and disable the Windows Firewall (for testing connectivity)
<img width="1373" alt="Screenshot 2024-09-10 at 11 31 20 AM" src="https://github.com/user-attachments/assets/689120ca-27ef-41f1-aecf-0064fea6cec0">
<img width="1373" alt="Screenshot 2024-09-10 at 11 31 56 AM" src="https://github.com/user-attachments/assets/bdec37e6-613f-437e-b520-595be7097c31">
![Uploading Screenshot 2024-09-10 at 11.32.01 AM.png…]()
<img width="1373" alt="Screenshot 2024-09-10 at 11 32 33 AM" src="https://github.com/user-attachments/assets/c7f92306-53db-4632-97b2-47a09bbdb3fd">

Setup Client-1 in Azure
—
Create the Client VM (Windows 10) named “Client-1”

* Username: labuser
* Password: Cyberlab123!
Attach it to the same region and Virtual Network as DC-1
After VM is created, set Client-1’s DNS settings to DC-1’s Private IP address
From the Azure Portal, restart Client-1
Login to Client-1
Attempt to ping DC-1’s private IP address
* Ensure the ping succeeded
From Client-1, open PowerShell and run ipconfig /all
* The output for the DNS settings should show DC-1’s private IP Address

</p>
<p>
  Winthin Azure create a resource group for your resouces and have it named "Active-Directory"and have resource group located in your region.Next create a virtual network and subnet, and then go to virtual matchine and create it nameing it DC-1(for domain controller).Make sure the OS is operating as WINDOWS SERVER 2022, and username and password"anything thats good for you to remember" then hit review and create and create.After the vm is created set the network ip address to static and login and disable firewall.Now that the Domain Controller(Admin ACC) is created rinse and repeat for a Client VM with minor differences like, OS will be an Windows 10 system name it client-1 and make sure to attach vm to the same region and Vnet as DC-1.
</p>
<br />

<h2>Step 2 Deploying Active Directory and create Admin Account<h2>
  
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
  Completed
Now that Vms are extablished we are going to install active directory domain services and promote DC-1 as an actual DC"im going to setup a new forest as mydomain.com" then restart DC-1. now that its a actual DC the username to get into DC-1 vm is now mydomain.com\labuser"password still the same"and now that ACTIVE DIRECTORY is installed we are going to add a domain admin user with the domain.Going to Active directory users and computers create an organzation unit name emplyees and one name admins now we are going to create an admin(JANE DOE WILL BE MY DOMAIN ADMIN) username will be Jane_admin with a password of choosing.But because jane_admin is added to admins folder its not yet an admin untill we add jane_admin to SECURITY GROUPS,then after that log out of DC-1 AND Log backin as mydomain.com\jane_admin, and that will be our new admin account.Now login to Client-1 vm with original credintals and join it to the domain vm will restart,and after that log into DC-1 and verify Client-1 shows up in computers and Create a new Organization unit file and name it _Clients and drag Clinet-1 into there.
</p>
<br />
<h2>Step 3&4 add users via powershell and simulate password lockout and disable<h2>
<img width="1225" alt="Screenshot 2024-09-10 at 5 52 25 PM" src="https://github.com/user-attachments/assets/1d293081-c11a-4aad-aadf-18478835baf5">
<img width="1225" alt="Screenshot 2024-09-10 at 5 52 35 PM" src="https://github.com/user-attachments/assets/e3cc2852-1b0c-4a91-8dbf-6c03d4acac3f">
<img width="1225" alt="Screenshot 2024-09-10 at 5 52 44 PM" src="https://github.com/user-attachments/assets/b8e8188f-5363-47c3-936f-a14b6bda8836">
<img width="1225" alt="Screenshot 2024-09-10 at 5 53 25 PM" src="https://github.com/user-attachments/assets/fd2b35aa-3a27-4a34-9be9-6769a60c34d6">
<img width="1225" alt="Screenshot 2024-09-10 at 5 53 25 PM" src="https://github.com/user-attachments/assets/658e6260-ce9a-4cf5-9aaa-5278ea3ca2fd">
  <img width="1225" alt="Screenshot 2024-09-10 at 5 53 37 PM" src="https://github.com/user-attachments/assets/ada35f74-cc45-432f-adf4-d59bd3cbf54b">
<img width="1225" alt="Screenshot 2024-09-10 at 5 53 47 PM" src="https://github.com/user-attachments/assets/7878c4ce-a39e-428a-9c86-466066bc3bd8">
<img width="1225" alt="Screenshot 2024-09-10 at 5 53 59 PM" src="https://github.com/user-attachments/assets/4bfd7a3b-3823-4ec9-b7ac-4c70082c48f7">
<img width="1225" alt="Screenshot 2024-09-10 at 5 54 11 PM" src="https://github.com/user-attachments/assets/9d95fe03-31ab-42e6-bd57-a0eda6555813">
<img width="1225" alt="Screenshot 2024-09-10 at 5 54 15 PM" src="https://github.com/user-attachments/assets/1aab08b3-4657-44d5-8605-b73182a1dbd3">
<img width="1225" alt="Screenshot 2024-09-10 at 5 56 10 PM" src="https://github.com/user-attachments/assets/0e9ec384-6f62-49fe-99e4-c388a24c647b">
<img width="1225" alt="Screenshot 2024-09-10 at 5 56 18 PM" src="https://github.com/user-attachments/assets/c36b4448-c836-4081-aacb-42113afc87d3">
<img width="1225" alt="Screenshot 2024-09-10 at 5 56 48 PM" src="https://github.com/user-attachments/assets/080e5ced-e16e-48c8-bd02-fafb5e899f7f">
<img width="1225" alt="Screenshot 2024-09-10 at 5 57 43 PM" src="https://github.com/user-attachments/assets/0c6e4920-406d-4d55-8087-9b428f179068">
<img width="1225" alt="Screenshot 2024-09-10 at 5 57 58 PM" src="https://github.com/user-attachments/assets/8769ff74-da7c-4ccb-acdb-5bd8b467d3a9">
<img width="1225" alt="Screenshot 2024-09-10 at 5 59 51 PM" src="https://github.com/user-attachments/assets/af2a095a-3075-4e54-8d20-e0eccfb9c16c">
<img width="1225" alt="Screenshot 2024-09-10 at 6 00 21 PM" src="https://github.com/user-attachments/assets/103decf3-bc41-4ad9-aa44-9b08401f16cb">
<img width="1225" alt="Screenshot 2024-09-10 at 6 01 13 PM" src="https://github.com/user-attachments/assets/3701883f-ff49-417f-86ce-0f2b081b48a2">
<img width="1225" alt="Screenshot 2024-09-10 at 6 01 36 PM" src="https://github.com/user-attachments/assets/4ef8ba99-184f-45d1-81bd-9f2ac56369f0">
<img width="1225" alt="Screenshot 2024-09-10 at 6 01 44 PM" src="https://github.com/user-attachments/assets/8cda5dd3-aa5a-4589-866a-d8646a52f16a">
<img width="1225" alt="Screenshot 2024-09-10 at 6 02 04 PM" src="https://github.com/user-attachments/assets/f1425c10-3a60-458a-ab96-8bb3a892ed36">

</p>
<p>
  Completed
Now that Client-1 is established as mydomain.com/jane_admin, login to client-1 using those credentials, open system properties, click remote desktop,allow domain users to access to remote desktop.you can now login to Client-1 as a normal, non administator user now.Next we are going to create a bunch of additional users using Powershell putting in a script and attempt to login to client-1 with one of the gernerated users,users will populate under _Employees in Active directory. Take one of the random generated accounts and lock self out, and then observe that account has been locked out within active directory and unlock account, reset password, attempt to login with it, and finally enable and disable accounts.
</p>
<br />
