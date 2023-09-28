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

<p align="left">
The goal of this project is to create a networking environment in VirtualBox that has the properties displayed in the image below. The creation of two virtual machines will be observed, the first of which will act as our domain controller (initialized as DC). This domain controller will be given two Network Adapters, one of which will connect to the internet and the other will be used for the internal network. The second virtual machine, which will be used to represent the client, will also connect to the internal network. After our DC is created, we will install Windows Server 2019 and assign IP Adressing for the internal network. The external IP Adressing will take place automatically because it will be assigned by our home router, or whichever router we are connected to at the time. We will then install Active Directory and create a domain and configure Network Address Translation so that clients will be able to connect to the internet. We will utilize PowerShell to create about 1,000 sample user accounts in our Active Directory environment. The second virtual machine will be installed with Windows 10. We will connect this machine to the domain and we will log into it using one of the generated domain accounts.  : <br/>
 
![Picture2](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/dd676e83-b80d-4afc-825d-637b01c6ddeb)


<br />
<br />
After we download VirtualBox and create the first virtual machine, it is time to set up our IP Addressing for our internal network. The NIC facing the internet will be automatically supplied with DHCP information from our home router. By navigating to our ethernet settings page we can change our adapter settings. There should be two network connections displayed based on how we configured the virtual machine in VirtualBox before launching it. You can open the status bar for each connection to determine whether it is the internet facing NIC or the internal network NIC and rename them accordingly. Under our internal network, we can click properties and adjust out IPv4 address to match the one set out in the diagram, which is 172.16.0.1:   <br/>

![VirtualBox_DC_27_09_2023_12_50_35](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/5e6cc0c4-71d6-4d8b-9c72-14a774ac4326)

<br />
<br />
The next task is renaming the PC. This can be done through System Settings under the section About Your PC. <br/>

![VirtualBox_DC_27_09_2023_13_00_28](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/7b863731-860b-41fa-a89c-7356f5aa0de0)

<br />
<br />
Our next step is to install Active Directory and create a domain. In order to do this we can navigate to the Add Roles and Features wizard and select Active Directory Domain Services. After we click add features a checkmark should appear next to the highlighted text in the image below. After this is installed we need to configure our post-installation settings. To do this we navigate to the notifications bar in the Server Manager and click the blue text "promote this server to a domain controller" which will open the Active Directory Domain Services Configuration Wizard. We then select "Add New Forest" and choose a domain name. After installation is complete the PC will restart.   <br/>

![VirtualBox_DC_27_09_2023_13_16_45](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/1057b062-cb54-4fd3-a333-0f2523b06202)

![VirtualBox_DC_27_09_2023_13_28_07](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/2c6a2ff9-1046-4d33-bfbb-30738aae3448)

<br />
<br />
We will now create our own dedicated domain admin account by navigating to Windows Administrative Tools and selecting the Active Directory Users and Computers option. Within the window we can right click on the domain we created in order to create a new organizational unit to put our domain admin account in. Once the organizational unit is created we right click on the unit to create a new user (our admin account). After the account is created it will show on the right side of the window. We then right click it and select properties in order to change it to an admin account by making it a MemberOf the previous admin group we created. If we log out of our current account we should now be able to log back in using our domain admin credentials that we just created.  <br/>

![VirtualBox_DC_27_09_2023_15_34_19](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/3d7075e8-6440-49ec-bbc4-5e45fd21a5d5)

![VirtualBox_DC_27_09_2023_15_35_43](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/51922eea-e43a-407f-8a85-3448c2611b4a)

![VirtualBox_DC_27_09_2023_15_41_35](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/9c790f78-1e96-41d4-b1cd-859ad6d11b80)

<br />
<br />
After we are logged into our admin account we are going to implement Remote Access Server and Network Address Translation on our Domain Controller. This will allow our client PC to be located on the internal network while still being able to acess the internet through our Domain Controller. To accomplish this we will go to Add Roles and Features within the Server Manager and select Remote Access. After it is installed we can go to the tools menu in the Server Manager and select Routing and Remote Access. Right click the DC (local) and select Configure and Enable Routing and Remote Access in orderr to install NAT. Then select our proper internet-facing Network Interface when prompted.     <br/>

![VirtualBox_DC_27_09_2023_15_49_41](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/90e41552-46f5-4ee6-9394-6f92566bafed)

![VirtualBox_DC_27_09_2023_16_07_38](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/58e2cefe-99f2-4319-8335-cab6394caf57)

<br />
<br />
Our next step is to set up a DHCP server on our Domain Controller which will set up IP Adresses and other DHCP information on our client PC. We again select Add Roles and Features within the Server Manager but this time we select DHCP. After it is installed we now need to configure DHCP options to the ones specified in our diagram. Go to Tools and select DHCP. Right click on IPv4 and select New Scope. Configure the options with the scope information provided in the diagram.     <br/>

![VirtualBox_DC_27_09_2023_16_12_27](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/7cca21f3-d4cb-4d65-a7e7-3e927cf638f3)

![VirtualBox_DC_27_09_2023_16_27_07](https://github.com/aleary1212/Active-Directory-Home-Lab/assets/67345075/8c757645-84d6-417b-8e5a-6f3c0991ed49)

<br />
We are now going to create users in the Active Directory environment using the follwing PowerShell script generated by Josh Madakor. Download the zip file using internet explorer on the virtual machine and save it to the desktop. Open the zip file and you should see a txt file containing a bunch of names and add our name to the top of the list. Now open PowerShell ISE as an Administrator by right-clicking on the icon or using PowerShell. Once inside, go ahead and open the CREATE USERS script from the folder. In order to enable the execution of scripts we need to input the following command into PowerShell "Set-ExecutionPolicy Unrestricted". Basically what this script is going to do is create a new organizational unit called Users and take all of the names from the names.txt file and create user accounts for all of them, all of which will use the same password. After running the script we should see all of the new users being created in PowerShell.
<br/>

<br />
The final step of this project is to create our client PC and implement Windows 10 in VirtualBox. When provisioning this virtual machine in VirtualBox be sure to select Internal Network in Network Settings instead of the default NAT. When installing Windows 10, select the Windows 10 Pro option instead of the default Windows Home. After Windows is installed the first thing we want to do is make sure the internet is working by going to the command line and entering ipconfig to see our configuration. Next we should ping google.com to verify that we can connect to the internet. With that, our entire diagram is set up and working. We can also add this client PC to our domain by navigating to Rename this PC (advanced) in Settings and inputting mydomain.com as the MemberOf value.
<br/>
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
