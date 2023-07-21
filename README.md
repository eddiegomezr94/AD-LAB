<p align="center">
<img src="https://imgur.com/M9CFO5o.png" width="300" height="200"/> >
</p>

<div align="center">
<h1> Active Directory Domain Services Install </h1>
</div>
This tutorial outlines the prerequisites, installation, and internal use of Active Directory Domain Services in Azure virtual machines. This includes making two seperate virtual machines, one for the Domain Controller Database, and the other for a Client wanting to use the domain services for their company. The lab shows how to configure new admins and users to be able to connect from the Domain Controller to the Client.

<h2> Environments and Technologies Used</h2>
 
  - Microsoft Azure 
  - Remote Desktop
  - Active Directory Domain Services
  - Windows Firewall

<h2> Operating System Used</h2> 

 - Windows Server 2022 Data Center: Azure Edition
 
 - Windows 10 (21H2)

<h2> List of Prerequisites</h2>

- Create Domain Controller (DC)

- Create Client Vitual Machine (VM)

<h2> Post VM Steps </h2>

- Set DC-1 Private IP to Static

- Ping DC-1 from Client-1

- Enable ICMPV4 IN DC-1 FireWall

- Client-1 Ping Reply

- Configure AD Domain Services

- Configure New Forest/Domain

- Configure Organizational Units

- Configure New Admin/New Users

- Test Client-1 DNS

- Change Client-1 DNS Azure

- Configure Client-1 Domain to DC-1

- Admin login from DC-1 to CLient-1

- DC-1 Power Shell USer Generator

- Client-1 DOmain User Access

- Sign in as User

<h2> Prerequisete Steps </h2> 

<Div align="center">
<H3> Domain Controller VM Created in Azure </H3>
</Div>
<p align="center">
<img src=https://imgur.com/wC0CD1r.png>
</p>

- The first step was to set up the Domain Controller VM named (DC-1) with its own Resource Group in Azure. This is the controller that will contain Active Directory's Database within the VM.

<Div align="center">
<H3> Client VM Created in Azure </H3>
</Div>
<p align="center">
<img src=https://imgur.com/f1lQ3JB.png>
</p>

- The second step was to create the Clients VM named (Client-1) using Windows 10 operating system as suggested by the client which is connected to the same Resource Group as DC-1.  It is important for the VM's to be in the same Resource Group as it will connect it to DC-1's V-net, if not in the same Resource Group Client-1 will not have acces to the network. The image above shows that they share the same V-net.

<h2> Post VM Creation Steps </h2> 

<Div align="center">
<H3> DC-1 Private IP Set Static </H3>
</Div>
<p align="center">
<img src=https://imgur.com/eNXKb1S.png>
</p>

- After the VM's are created and inspected to be sharing the same virtual network the next step was to set DC-1's private IP adress to static. Initially it is dynamic but the reason to set to static is so that the VM does not change its IP adress when installing the new Domain in the steps ahead.  This will keep the Private IP adress normal at 10.0.0.4 without any new installations affecting the adress.

<Div align="center">
<H3> Perpetual Ping Test </H3>
</Div>
<p align="center">
<img src=https://imgur.com/C1vRxGc.png>
</p>

- The next step was to log in to Client-1 VM and perpetually ping DC-1's private IP in order to see if there was a reply.  This was to see if DC-1 allowed Client-1 to recieve diagnostics that came from DC-1. Apparently the Fire Wall in DC-1 did not enable Client-1 to recieve diagnostics as shown above.

<Div align="center">
<H3> DC-1 ICMPV4 Fire Wall Enabled </H3>
</Div>
<p align="center">
<img src=https://imgur.com/1qhIv9P.png>
</p>

- The step that follows shows the enablement of DC-1's IMPV4'S Network Diagnostics within Windows Defender Firewall.

