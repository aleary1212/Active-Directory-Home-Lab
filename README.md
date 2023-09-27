<h1>Active Directory Home Lab</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
Project consists of creating an Active Directory environment utilizing Oracle VirtualBox.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
The goal of this project is to create a networking environment in VirtualBox that has the properties displayed in the image below. The creation of two virtual machines will be observed, the first of which will act as our domain controller (initialized as DC). This domain controller will be given two Network Adapters, one of which will connect to the internet and the other will be used for the internal network. The second virtual machine, which will be used to represent the client, will also connect to the internal network. After our DC is created, we will install Windows Server 2019 and assign IP Adressing for the internal network. The external IP Adressing will take place automatically because it will be assigned by our home router, or whichever router we are connected to at the time. We will then install Active Directory and create a domain and configure Network Address Translation so that clients will be able to connect to the internet. We will utilize PowerShell to create about 1,000 sample user accounts in our Active Directory environment. The second virtual machine will be installed with Windows 10. We will connect this machine to the domain and we will log into it using one of the generated domain accounts.  : <br/>
![Picture1](AD_Images/https://github.com/aleary1212/Active-Directory-Home-Lab/tree/main)

<br />
<br />
After we download VirtualBox and create the first virtual machine, it is time to set up our IP Addressing for our internal network. The NIC facing the internet will be automatically supplied with DHCP information from our home router. By navigating to our ethernet settings page we can change our adapter settings. There should be two network connections displayed based on how we configured the virtual machine in VirtualBox before launching it. You can open the status bar for each connection to determine whether it is the internet facing NIC or the internal network NIC and rename them accordingly. Under our internal network, we can click properties and adjust out IPv4 address to match the one set out in the diagram, which is 172.16.0.1:   <br/>
<img src="https://i.imgur.com/tc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The next task is renaming the PC. This can be done through System Settings under the section About Your PC. <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Our next step is to install Active Directory and create a domain. In order to do this we can navigate to the Add Roles and Features wizard and select Active Directory Domain Services. After we click add features a checkmark should appear next to the highlighted text in the image below. After this is installed we need to configure our post-installation settings. To do this we navigate to the notifications bar in the Server Manager and click the blue text "promote this server to a domain controller" which will open the Active Directory Domain Services Configuration Wizard. We then select "Add New Forest" and choose a domain name. After installation is complete the PC will restart.   <br/>
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
