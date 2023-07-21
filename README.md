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

- Test Client-1 Access to DC-1 Domain Services

- IPConfigure Check Client-1

- Change Client-1 DNS Azure

- CLient-1 IPConfig Check DNS

- Client-1 Domain Name Change Successfully

- Admin login from DC-1 to CLient-1

- DC-1 Power Shell USer Generator

- Client-1 Domain User Access

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

- After the VM's are created and inspected to be sharing the same virtual network the next step was to set DC-1's private IP address to static. Initially it is dynamic but the reason to set to static is so that the VM does not change its IP address when installing the new Domain in the steps ahead.  This will keep the Private IP address normal at 10.0.0.4 without any new installations affecting the address.

<Div align="center">
<H3> Perpetual Ping Test </H3>
</Div>
<p align="center">
<img src=https://imgur.com/C1vRxGc.png>
</p>

- The next step was to log in to Client-1 VM and perpetually ping DC-1's private IP (10.0.0.4) in order to see if there was a reply.  This was to see if DC-1 allowed Client-1 to recieve diagnostics that came from DC-1. Apparently the Fire Wall in DC-1 did not enable Client-1 to recieve diagnostics as shown above.

<Div align="center">
<H3> DC-1 ICMPV4 Fire Wall Enabled </H3>
</Div>
<p align="center">
<img src=https://imgur.com/1qhIv9P.png>
</p>

- The step that follows shows the enablement of DC-1's IMPV4'S Network Diagnostics within Windows Defender Firewall.

<Div align="center">
<H3> Perpetual Ping Test Working </H3>
</Div>
<p align="center">
<img src=https://imgur.com/ldnaWYv.png>
</p>

- This next step shows Client-1 perpetual ping from before now recieving request from DC-1's private IP address successfully.

<Div align="center">
<H3> Active Directory Domain Services Install </H3>
</Div>
<p align="center">
<img src=https://imgur.com/eOqzbk2.png>
</p>

- Within the next step is the installation of the Domain Services within Active Directory. You begin by Adding Roles and Features ->  Check Active Directory Domain Services -> Hit next until Install.

<Div align="center">
<H3> Configure New Forest/Custom Domain </H3>
</Div>
<p align="center">
<img src=https://imgur.com/R6kvsZN.png>
</p>

- The next initial step shows how to complete the installation of the clients personalized domain service. For this most part this step just includes the personalized domain name the clietn wants and password used to access the domain systems database.

<Div align="center">
<H3> Configure Organizational Units </H3>
</Div>
<p align="center">
<img src=https://imgur.com/qGts2bc.png>
</p>

- After creating the domain the next step was to provide the client new organizational units named _ADMINS and _EMPLOYEES. To do this within AD go to Tools-> Users and Computers -> Right Click Custom Domain -> Add Organizational Unit -> Name _ADMINS. Repeat same process for _EMPLOYEES.

<Div align="center">
<H3> Configure New Admin/Users </H3>
</Div>
<p align="center">
<img src=https://imgur.com/ePC8832.png
</p>

- Once the Organizational Units are made the next step was to add Jane to the Admins group. to do this go to _ADMINS group -> right click to add new user -> input name, login name, and user password. This only makes them a new user, so in order to assign them to the domain admins right click on Janes name -> Properties -> Member of -> Add -> Type in Domain Admins -> OK -> Set Primary Group to Domain Admins. This now alows Jane to access both VM's as an Administrator.

<Div align="center">
<H3> Client-1 DNS Test </H3>
</Div>
<p align="center">
<img src="https://imgur.com/6WTsAOn.png" width="400" height="500"/>
</p>

- After creating the profile for the Admin and Users, the next step was to test if Client-1 was able to join the Domain automatically. In order to check was to go into Client-1 -> Right Click Windows -> System -> Rename this PC -> Computer Name -> Name/Domain Change -> Input DC-1's Domain -> Failed Connection. This step was done in this lab in order to get used to checking the DNS servers that connect both VM's to the domain.

<Div align="center">
<H3> Client-1 IPConfig Check DNS </H3>
</Div>
<p align="center">
<img src="https://imgur.com/e4BIR9w.png"/>
</p>

- This next step shows how to check if Client-1's DNS was connected to DC-1'S private IP. To do this type ipconfig/all to check all of Client-1s connections. In this case there was no connection to DC1's address 10.0.0.4 in the DNS section.

<Div align="center">
<H3> Configure Client-1 DNS to DC-1 </H3>
</Div>
<p align="center">
<img src="https://imgur.com/TdSqBTX.png"/>
</p>

- In order for Client-1 to access the domain created in DC-1 the Clients DNS needs to be changed manually in the Azure portal. To do this go to CLient-1 VM in Azure -> Newtorking -> DNS -> Custom -> Apply DC-1 Private IP (10.0.0.4) -> Click Save -> Restart Client-1 VM within Azure. It is important to restart the VM if not this step wont work.

<Div align="center">
<H3> CLient-1 IPConfig Check DNS </H3>
</Div>
<p align="center">
<img src="https://imgur.com/CoRANBk.png"/>
</p>

- After manually changing CLient-1's DNS and refreshing the VM the next action step is to log in to CLient-1 and check IPConfig to see if the DNS changed to DC-1's private IP. Under DNS it showss the private IP (10.0.0.4), therefore it is connected to DC-1's private IP.

<Div align="center">
<H3> Client-1 Domain Name Change Successfully </H3>
</Div>
<p align="center">
<img src="https://imgur.com/YCAMmwf.png"/>
</p>

- Once checking to see if DNS matches DC-1's Private IP one is able to change Client-1's Domain name and connect it to DC-1's server. Follow steps before when attempting to change Client-1's Domain ,begin by logging in Client-1 VM -> Right Click Windows -> System -> Rename this PC -> Computer Name -> Name/Domain Change -> Input DC-1's Domain -> Input Admin username and password -> in return it should succeed and restart the VM. This is done so the Admin and Users can be connected to and be able to log in to CLient-1 VM.

<Div align="center">
<H3> Admin login from DC-1 to CLient-1 </H3>
</Div>
<p align="center">
<img src="https://imgur.com/Q2DPYBQ.png"/>
</p>

- When VM restarts one should be able to successfully log in to Client-1 VM. This Just SHows that it is now possible for an Admin created in DC-1's Active Directory system can log into Client-1. This demonstrates how to connect both VM' and now Admins have access to Client-1's system.

<Div align="center">
<H3> DC-! Power Shell User Generator </H3>
</Div>
<p align="center">
<img src="https://imgur.com/jftAx9c.png"/>
</p>

- The next step was to generate new Users within DC-1's Domain Services. This was done to generate a long list of employees for the Client each with the same password and had the ability to change the password once logging on.  To do this one would use PowerShell ISE and input a given script that would generate over 1,000 employees with their personal username. Pretty fun step.

<Div align="center">
<H3> Client-1 Domain User Access </H3>
</Div>
<p align="center">
<img src="https://imgur.com/RxJyAQi.png"/>
</p>

- In order for Users to access and login to Client-1's System one has to allow all Users being created access.  To do this go into Client-1 VM -> Right Click Windows -> System -> Remote Desktop -> Select Users to Access -> Lookup Domain Users -> Click OK. Now all Users have access to Client-1 and can remotely access.







