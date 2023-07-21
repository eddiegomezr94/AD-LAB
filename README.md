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
  <H1> Domain Controller VM Created in Azure </H1>
  </Div>
  <p align="center">
  <img src=https://imgur.com/wC0CD1r.png>
  </p>

- The first step was to set up the Domain Controller VM named (DC-1) with its own Resource Group in Azure. This is the controller that will contain Active Directory's Database within the VM.

    <Div align="center">
  <H1> Domain Controller VM Created in Azure </H1>
  </Div>
  <p align="center">
  <img src=https://imgur.com/f1lQ3JB.png>
  </p>

- The second step was to create the Clients VM named (Client-1) using Windows 10 operating system as suggested by the client which is connected to the same Resource Group as DC-1.  It is important for the VM's to be in the same Resource Group as it will connect it to DC-1's V-net, if not in the same Resource Group Client-1 will not have acces to the network. The image above shows that they share the same V-net.  
