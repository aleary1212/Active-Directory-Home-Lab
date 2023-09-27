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
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tc" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
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
