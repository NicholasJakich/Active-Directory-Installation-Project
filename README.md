# Active Directory Installation and Implementation through Azure

![55F9F1FF-AE40-437B-88BB-25EE7689BD27](https://github.com/user-attachments/assets/49cc6633-30a8-442a-ac80-b25ea3861936)

**Summary**

This tutorial project outlines how to install Active Directory through Microsoft Azure and some examples of using AD through its accounts and security features. This main section shows the process of installing Active Directory using Azure, using one client Virtual machine, and one VM for Domain controller. The second section of the project shows Active Directory Group Policy and account security features.  <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure Account
- A working computer
- Virtual Machines in Azure
- Powershell (in VMs)
- Windows OS (in VMs)
- Required software: Active Directory Domain Services, Domain controller, and Remote Desktop 


<h2>Steps for Project - Installation of Active Directory using Azure </h2>



1. Using Microsoft Azure, create a Resource Group for the Active Directory VMs and create a Virtual Network. To do so, click Resource Group, name the group, and click create. Search for Virtual Network in the search bar, and follow the same steps to create one.

![8A188B03-92C5-4F24-BA5F-98AA950E4700_4_5005_c](https://github.com/user-attachments/assets/bcab40a2-ce8e-4608-9760-8685aa9fbab5)

2. Create two Virutal machines. This includes one for a client machine and a Domain Controller Machine. In this project the VMs are known as Client 1 and DC 1.

![8455CADF-A5BE-4242-AE11-F09ADBE5BBF6](https://github.com/user-attachments/assets/c4180ede-bab0-49fc-b1fd-e45db40eb74b)

3. Using Remote desktop, sign into the Virtual machines. First sign into the Domain Controller VM and disable the Windows firewall. This is done by going to Windows Defender Firewall setting, uncheck the to turn them off, and click apply.

![178B820E-80E5-4388-A753-1C9E284E6270](https://github.com/user-attachments/assets/dbb0c440-77ce-4edb-85f4-1265ba1a8e44)

4. In Azure in the Domain controller VM (DC-1), copy the VM's private IP address. Go to the setting for Client 1 and paste the IP address to the DNS server in Client 1. This allows the ability to join the domain.

<img width="662" alt="38544F13-FCC1-49EE-AB11-62B76A20B035" src="https://github.com/user-attachments/assets/cd994989-dc74-4f7f-95ca-a9eee522c1b0" />


5. Restart the VM and open the Client 1 VM. Within the OS, open powershell and ping the IP address of DC 1. This allows you to check and confirm the ping that Client 1 is using DC 1 as the DNS server.

![C7450D31-1407-41ED-9BDE-FF6888EF90D1](https://github.com/user-attachments/assets/93510ad1-ac82-47f3-92bb-617a15aae6c1)

6. In the DC 1 VM, go to Server Manager through the Windows search bar. From Server Manager activate Active Directory Domain Services by clicking the option to install it.

![image](https://github.com/user-attachments/assets/7842cabd-f899-4200-8e65-85c49e88e84a)

7. In Server Manger setting, click the flag icon and open the ADDS Configuration Wizard. Within that settiing, complete the setting for the Domain name, Forest, and install. Afterwards, restart the VM. This makes the OS a Domain controller.

![image](https://github.com/user-attachments/assets/74b0bd25-dcd9-4b1b-87ec-799857614dff)


8. Within the DC 1 Virtual Machine, go to Windows Administrative tools and choose Active Directory Users and Computers. From here, Organizational Units and User accounts can be created in this setting for Active Directory.

![D81EC8BA-029D-4CE4-B3F7-3404B22EC981](https://github.com/user-attachments/assets/aedae524-2658-4b19-b6fc-6173f5466c56)

9. It is reccomended to create a User Account and make it the Domain's Admin so it can edit and have more permissions. To do so, click Admins and create a new user. Create a name, password, and choose Finish. After the account is made, right click to choose properties and move the account into the Domain Admins group to make it an Administator.

<img width="1085" alt="D936C535-CEF7-4A05-BF91-1D5EEA684A41" src="https://github.com/user-attachments/assets/8e2d0ae1-473a-4dce-ae78-0218441a18ad" />

10. Log in to the Client VM (Client 1) to make it part of the Domain from the Active Directory. To do so, right-click Start, click System, and click Rename this PC (advanced). From this menu, the Client 1 can be made part of the Active Directory Domain. Additionally a Domain Admin account should be used to sign in to finish this step, and restart the VM to complete the process.

![175CD613-6D23-455A-B5C4-0BAB1E8176D3](https://github.com/user-attachments/assets/de417855-2e9f-41d5-908e-d404c39dff3e)


<h2> Basic Group Policy and Account Permissions </h2>

Using setting such as Group Policy Management Console, certain permissions and policy can be set. The Group Policy is part of Active Directory and can configure accounts in ADDS. This section shows how to use security features like locking out an account from too many wrong password attempts, and reseting a password.

1. To get to Group Policy within a Windows OS, right click Start, click Run, type gpmc.msc, and hit the enter key. This is how to get to the Group Policy Management Console.

![B38350F0-B10B-422E-A950-AC1F99664260](https://github.com/user-attachments/assets/46001f11-0d0a-4df8-8d8a-8966a76d4c48)

2. Open the Account Lockout setting. To do so, click and open the following: Computer Configuration > Policies > Windows Settings > Security Settings > Account
Policies > Account Lockout Policy.

<img width="675" alt="5CC4144F-0138-4A8A-88B7-E04D6775E6F4" src="https://github.com/user-attachments/assets/d34a745d-4f1c-481e-a75a-04e8dd78905f" />

3. From Account Lockout Policy, settings can be chosen to add security to an account. An example is choosing account lockout and setting it to 20 attempts. This locks an account after 20 wrong attempts. Account lockout duration can be set to how long to wait before an account can be log in again.

<img width="727" alt="1024062B-360F-4D55-A39C-0FE38F211CB8" src="https://github.com/user-attachments/assets/61a0bc98-141c-44be-820a-e49d4a0c7a3a" />

4. Ater appliying new group policy setting, the the account security can be checked. Sign out, refresh, and try to sign in with the wrong password by the number of attempts used in the setting. The account should lock out for a while, showing the features worked for extra security.

![F4827B1C-0D1B-4778-B917-9E4BDB88460F](https://github.com/user-attachments/assets/31e80b0f-b23c-4a8c-9fbf-a3e6e4ca20ad)

5. The password for an account can also be changed from Active Direcory Users and Computers setting. Simply right click an account, choose reset password, and create a new password from that section and click OK. From this section you can also unlock the user's account.

![FF0F6844-B388-433E-A6C6-FDCBC9C482C7](https://github.com/user-attachments/assets/14a869df-27b8-4d2a-a85e-ee9be4b0b4d2)

