# Active Directory Installation and Implementation through Azure

![55F9F1FF-AE40-437B-88BB-25EE7689BD27](https://github.com/user-attachments/assets/49cc6633-30a8-442a-ac80-b25ea3861936)

This tutorial project outlines how to install Active Directory through Microsoft Azure. It shows the process of installing and some examples of using AD through its accounts and features.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure Account
- A working computer
- Virtual Machines in Azure
- Windows OS
- Required software: Active Directory Domain Services, Domain controller, and Remote Desktop 


<h2>Steps for Project - Installation and Account Permission Features</h2>


Creating VMs, Resource group in Azure, Virtual Network, one VM is Client 1 and one is Domain controller.

1.Using Microsoft Azure, create a Resource Group for the Active Directory VMs and create a Virtual Network. To do so, click Resource Group, name the group, and click create. Search for Virtual Network in the search bar, and follow the same steps to create one.

![8A188B03-92C5-4F24-BA5F-98AA950E4700_4_5005_c](https://github.com/user-attachments/assets/bcab40a2-ce8e-4608-9760-8685aa9fbab5)

2.Create two Virutal machines. This includes one for a client machine (Client 1) and a Domain Controller Machine (DC 1).

![8455CADF-A5BE-4242-AE11-F09ADBE5BBF6](https://github.com/user-attachments/assets/c4180ede-bab0-49fc-b1fd-e45db40eb74b)

3.Using Remote desktop, sign into the Virtual machines. First sign into the Domain Controller VM adn disable the Windows firewall. This is done by going to Windows Defender Firewall setting, uncheck the to turn them off, and click apply.

![178B820E-80E5-4388-A753-1C9E284E6270](https://github.com/user-attachments/assets/dbb0c440-77ce-4edb-85f4-1265ba1a8e44)

4.In Azure in the Domain controller VM (DC-1), copy the VM's private IP address. Go to the setting for Client 1 and paste the IP address to the DNS server in Client 1. This allows the ability to join the domain.

<img width="662" alt="38544F13-FCC1-49EE-AB11-62B76A20B035" src="https://github.com/user-attachments/assets/cd994989-dc74-4f7f-95ca-a9eee522c1b0" />


5.Restart the VM and open the Client 1 VM. Within the OS, open powershell and ping the IP address of DC 1. This allows you to check and confirm the ping that Client 1 is using DC 1 as the DNS server.

![C7450D31-1407-41ED-9BDE-FF6888EF90D1](https://github.com/user-attachments/assets/93510ad1-ac82-47f3-92bb-617a15aae6c1)

6.In the DC 1 VM, go to Server Manager through the Windows search bar. From Server Manager activate Active Directory Domain Services by clicking the option and install

![image](https://github.com/user-attachments/assets/7842cabd-f899-4200-8e65-85c49e88e84a)

7.In Sever Manger setting, click the flag icon and open the ADDS Configuration Wizard. Within that settiing, complete the setting for the Domain name, Forest, and install. Afterwards, restart the VM. This makes the OS a Domain controller.

![image](https://github.com/user-attachments/assets/74b0bd25-dcd9-4b1b-87ec-799857614dff)


8.

9.

10.

