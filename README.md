<p align="center">
<img src="https://user-images.githubusercontent.com/123595654/219353683-95266159-08a0-4165-a5ed-cb9487a0670a.gif" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud ☁️  

<img src="https://user-images.githubusercontent.com/123595654/219356229-2859fb38-37ec-4593-9705-9cd05bcc8a53.gif" alt="Microsoft Active Directory Logo"/>
</p>

(Azure)</h1>
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

- Create two VMs inside of Azure, One named the Domain Controller or (DC-1) operating on (Windows Server 2022) & the other virtual machine named, “Client-1” operating on (Windows 10). 

- By doing this we will first create a resource group. Scroll upwards to the, "create resource group" tab or simply type it in the search bar. Once created, name the resource group, review it, and finalize it. When done scroll to, "create a virtual machine." Next, create the virtual machine and name it, "DC-1." Click the, "Plus" (+) button under, "Virtual machines" and fill out any information regarding the VM. Make sure the VM has the same region created with the resource group. Afterwards, create a login and password for the VM to further access that VM on a Remote Desktop. Once done, review and finalize the VM. Subsequently, repeat the process above and create another VM named, "Client-1." All VMs & resource groups should be under the same region and have the same defaulted vnet in their configurations. 

<img src="https://i.imgur.com/mVEFFjn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Set Domain Controller's NIC Private IP address from dynamic to static. 

- By doing this, type in virtual machines in the search bar and click on the domain controller VM. Scroll to networking on the left column & click it. Once it opens, press on the blue highlighted link next to the, "Network interface." Scroll to the left column under, "settings" and hit the, "IP configurations" tab. When it opens, scroll down and click the selected name of the IP. As soon as it opens, change the assignment from, "Dynamic" to "static" and press the save logo on top. 
</p>
<br />

<p>
<img src="https://i.imgur.com/7zCkC0T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure Connectivity between the client-1 & Domain Controller

- Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)

- By doing this we will get the public IP address from Client-1, copy and paste the IP address into the remote desktop application, and sign in. Do the same process for DC-1. Once logged into both remote desktops, navigate back to azure and copy the private IP address for DC-1. Once DC-1’s private IP address is copied, log into client-1’s remote desktop and open the command prompt. Once opened, ping the domain controller's private IP, resulting in (Ping -t (DC-1 PRIVATE IP)). After you press enter, you should receive a time-out message. This, “Time-out” message is due to the Domain controller's firewalls blocking the “ICMP” traffic. 


<img src="https://i.imgur.com/JfuKIrc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Login to the Domain Controller and enable ICMPv4 on the local windows Firewall
 
- We will go to the Domain controller's public IP address and copy it. Once copied, go into the remote desktop and log in with your credentials. Once you are signed in to DC-1’s desktop, click the windows icon at the bottom left or the start button and search wf.msc (Windows Defender Firewall). Once searched, open it and head to “inbound rules” located in the left column. Scan and find the category that falls under the protocol column. When you find the column scroll down until you locate ICMPv4. Verify it instates the name, “Core Networking Diagnostics-ICMP Echo Request”. After you locate it, enable both rows of “ICMP Echo Requests”. 


<img src="https://i.imgur.com/gJoKozF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Check back at Client-1's Remote Desk Top to see the ping succeed

- Once both of the “Core Network Diagnostics-ICMP Echo Requests” are enabled, check Client-1’s command prompt. The Domain controller's or (DC-1’s) reply sequence has ceased to timed out and has allowed the ICMP traffic to come through the firewalls. 

- Type in control C to stop the (Ping -t) from continuing. In conclusion, now that DC-1’s firewalls are allowing the ICMP traffic to proceed, there can be communication between Client-1 and the domain controller. 

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create an Admin & Normal User Account in Active Directory 

- Open the Active Directory Users and Computers console. You can do this by clicking on the Start button, selecting Administrative Tools, and then selecting Active Directory Users and Computers.

- Navigate to the container where you want to create the user accounts. This is typically the Users container in the domain.

- Right-click on the container and select New -> User. This will open the New Object - User wizard.

- In the first screen of the wizard, enter the user's first name, last name, and username. You can also enter a display name, which is what will appear in the Global Address List.

- In the second screen of the wizard, enter and confirm a password for the user.
In the third screen of the wizard, select the user's group membership. For an admin account, you will want to add the user to the Domain Admins group. For a normal user account, you can add the user to any appropriate groups based on their role.
 
- Click Next to review your selections, and then click Finish to create the user account. Once you've created the user accounts, you can set additional properties and configure any necessary permissions for the accounts. It's also important to regularly review user accounts and adjust their group membership and permissions as needed to maintain security and compliance.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Join Client-1 to your Domain (mydomain.com)

- To join a client computer to a domain (in this example, "mydomain.com"), follow these steps:

- Log in to the client computer (Client-1) using an administrator account.

- Open the Control Panel and navigate to System and Security -> System.
 
- Click on "Change settings" next to "Computer name, domain, and workgroup settings".

- Click "Change" next to "To rename this computer or change its domain or workgroup".

- Select the "Domain" option and enter the name of your domain (in this example, "mydomain.com"). Click "OK".

- Enter the credentials of a user account with permission to join a computer to the domain. This is typically a domain administrator account.

- Click "OK" to confirm the domain change and restart the computer when prompted.

- After the computer restarts, log in using an account from the domain (in this example, "mydomain.com").

Once the client computer (Client-1) is joined to the domain, you can configure various domain policies, manage user accounts and permissions, and perform other domain-related tasks from the domain controller or other administrative workstations. It's important to ensure that the client computer is properly secured and updated with the latest patches and antivirus software before joining it to the domain to minimize security risks.
</p>
<br />


<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Setup Remote Desktop for non-admin users on client-1

- To set up Remote Desktop for non-admin users on Client-1, follow these steps:

- Log in to Client-1 using an administrator account.

- Open the Control Panel and navigate to System and Security -> System.

- Click on "Remote settings" on the left-hand side of the screen.

- In the "Remote" tab, select "Allow remote connections to this computer" and choose the appropriate option for your network security.

- Click on "Select Users".

- Click on "Add" to add a new user account.

- Type the name of the non-admin user you want to grant remote access to and click "OK".

- Choose the appropriate option for the user's remote access permissions, either "Full Control" or "Remote Desktop Users".

- Click "OK" to confirm the user's remote access permissions.

- Close the Remote Desktop settings and log out of the administrator account.

After completing these steps, the non-admin user should be able to connect to Client-1 via Remote Desktop using their own credentials. Note that the non-admin user may need to install the Remote Desktop client software on their own computer if it's not already installed. Additionally, it's important to ensure that the non-admin user's account is properly secured and has the necessary permissions to perform remote tasks on Client-1 to minimize security risks.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create additional Users & attempt to log into Client-1 with one of the users 

- To create additional users and attempt to log into Client-1 with one of the users, follow these steps:

- Log in to Client-1 using an administrator account.

- Open the Control Panel and navigate to User Accounts -> Manage another account.

- Click on "Add a new user in PC settings".

- Enter the new user's email address or phone number and click "Next".

Choose whether to create a Microsoft account or a local account for the new user. If you choose to create a Microsoft account, the user will need to sign up for a Microsoft account if they don't already have one. If you choose to create a local account, you will need to set a username and password for the user.

- Click "Finish" to create the new user account.

- To log in to Client-1 with the new user account, log out of the administrator account and click on the "Other user" button on the login screen.

- Enter the username and password for the new user account and click "Sign in".

- If the login is successful, the new user account should be able to access the desktop and applications on Client-1.

Repeat steps 3-6 to create additional users as needed. It's important to ensure that each user account is properly secured and has the appropriate permissions to access the resources they need on Client-1.
</p>
<br />
