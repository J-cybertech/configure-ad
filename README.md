# WIN-DNS
<p align="center">
<img src="https://i.imgur.com/k3pK1RT.jpeg" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in VirtualBox</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Oracle VM VirtualBox Machines/Compute
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (22H2) 

<h2>Deployment and Configuration Steps</h2>

<p>
In this lab we will create two Virtual Machines (Vms) in the same Virtual-network. One will be a Domain Controller (WIN-DC1), the other will be a Client machine (WIN-Client1). We will change the DC to a static IP because its offering Active Directory services to the client machine. Client machine will join the domain. We will control the DNS settings on the client machine, the client machine will use the DC as its DNS server. 
</p>

<br />
<p>
<img src="https://i.imgur.com/hAcv65g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<P>
Once your finally in the server, install AD Users & Computers. Rename the VM computer name to WIN-DC1, setup a new forest as "hardwaretech.com" afterwards restart and then log back into DC1 user "hardwaretech.com\Administrator". Create a user so that you are able to login on Client1 pc with. 
</p>
<br />
<p>
<img src="https://i.imgur.com/Zl8eHHb.png" height="80%" width="80%" alt="Active Directory Users and Computers"/>


<p>
DC1 has to have a static Private IP Address (Class A - 10.0.2.15 : 255.0.0.0 : 10.0.2.2 ). Set the network settings on both VMs to Host-only Adapter. Client1 will connect to DC1 to ensure connectivity we will try to ping DC-1 from Client-1. At first the ping will not work correctly. We have to set IP for Client1 to 10.0.2.16, 255.0.0.0, 10.0.2.2; dns 10.0.2.15, 10.0.2.2. Now we can ping DC-1 successfully from Client-1. In Client1 pc head over to Computer Name/Domain Changes and under Domain enter the domain name (hardwaretech.com). Pc will restart and in the server Vm you will see Client1 inside Active Directory Users and Computers - Computers folder.
</p>
<br />

<br />
<p>
<img src="https://i.imgur.com/U0fu22I.png" height="180%" width="180%" alt="Ping Success"/>
<img src="https://i.imgur.com/2xKzXMC.png" alt="Domain Added"/>
<img src="https://i.imgur.com/wT0ukXA.png" alt="Computer Added to Server"/>
</p>

<p>
Lets add a user on the server by going onto Active Directory User and Computers, inside User folder you will right click on an empty space - New < User. Now login onto client1 vm with new user's credentials.
<img src="https://i.imgur.com/ewlIaXB.png" alt="User Login"/>
</p>
