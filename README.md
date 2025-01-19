# WIN-DNS

<p align="center">
![image](https://github.com/user-attachments/assets/5decd1dc-c4c9-4f64-851f-e2ea397f01ba)
!(https://github.com/user-attachments/assets/189e70eb-a82f-4c72-bd74-5aef002d8618)

</p>

<h1>On-premises Active Directory Deployed in the VirtualBox</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Oracle VM VirtualBox Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- [Windows Server 2022] (https://go.microsoft.com/fwlink/p/?LinkID=2195280&clcid=0x409&culture=en-us&country=US)
- Windows 10 Pro (22H2) 

<h2>Deployment and Configuration Steps</h2>

<p>
In this lab we will create two Virtual Machines (Vms) in the same Virtual-network. One will be a Domain Controller (WIN-DC1), the other will be a Client machine (WIN-Client1). We will change the DC to a static IP because its offering Active Directory services to the client machine. Client machine will join the domain. We will control the DNS settings on the client machine, the client machine will use the DC as its DNS server. 
</p>
<br />

<P>
Once your finally in the server, install AD Users & Computers. Rename the VM computer name to WIN-DC1, setup a new forest as "hardwaretech.com" afterwards restart and then log back into DC1 user "hardwaretech.com\Administrator". Create a user so that you are able to login on Client1 pc with. 
</p>
<br />
<p>
<img src="https://i.imgur.com/a/07jO9bo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>
<img src="https://i.imgur.com/d22FHIm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
DC1 has to have a static Private IP Address (Class C - 10.0.2.15 : 255.255.255.0 : 10.0.2.2 ). Set the network settings on both VMs to Host-only Adapter. Client one will connect to DC1 to ensure connectivity we will try to ping DC-1 from Client-1. At first the ping will not work correctly. We have to set IP for DC1 to 10.0.2.16, 255.255.255.0, 10.0.2.2; dns 10.0.2.15, 10.0.2.2. Now we can ping DC-1 successfully from Client-1. In Client1 pc head over to Computer Name/Domain Changes and under Domain enter the domain name (hardwaretech.com). Pc will restart and in the server Vm you will see Client1 inside Active Directory Users and Computers - Computers folder.
</p>
<br />
