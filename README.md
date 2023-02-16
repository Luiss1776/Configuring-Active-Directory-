<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud ☁️ (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used 🧑‍💻</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used  💻 </h2>

- Windows Server 2022
- Windows 10 🪟 (21H2)

<h2>High-Level Deployment and Configuration Steps 📝</h2>

- Configure Resources in Azure 
- Ensure Connectivity between the client-1 & Domain Controller 
- Create an Admin & Normal User Account in Active Directory 
- Join Client-1 to your Domain (mydomain.com)
- Setup remote desktop for non-admin users on client-1
- Create Users & attempt to login within an user 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/yyQUwSx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Configure Resources in Azure 

Create two VMs inside of Azure, One named the Domain Controller or (DC-1) operating on (Windows Server 2022) & the other virtual machine named, “Client-1” operating on (Windows 10). 

By doing this we will first create a resource group. Scroll upwards to the, "create resource group" tab or simply type it in the search bar. Once created, name the resource group, review it, and finalize it. When done scroll to, "create a virtual machine." Next, create the virtual machine and name it, "DC-1." Click the plus button under, "Virtual machines" and fill out any information regarding the VM. Make sure the VM has the same region created with the resource group. Afterwards, create a login and password for the VM to further access that VM on a Remote Desktop. Once done, review and finalize the VM. Subsequently, repeat the process above and create another VM named, "Client-1." All VMs & resource groups should be under the same region and have the same defaulted vnet in their configurations. 

<img src="https://i.imgur.com/mVEFFjn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Set Domain Controller's NIC Private IP address from dynamic to static. 

By doing this we will type in virtual machines in the search bar and click on the domain controller VM. Scroll to networking on the left column. Once it opens, click on the blue highlighted link next to the Network interface. Scroll to the left column under settings and hit the Ip configurations tab. When it opens, scroll down and click the selected name of the IP. Once it opens, change the assignment from Dynamic to static and press the save logo on top. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the Client-1 & Domain Controller 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create an Admin & Normal User Account in Active Directory 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Join Client-1 to your Domain (mydomain.com)

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup Remote Desktop for non-admin users on client-1

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create additional Users & attempt to log into Client-1 with one of the users 

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
