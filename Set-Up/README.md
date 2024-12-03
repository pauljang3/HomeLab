# Home Lab Set Up and Configuration

## Hardware Components  
For this project, I used my home PC with the following specs:

- Processor: Intel i7
- Memory: 16GB RAM
- Storage: 1TB SSD

---

## Software Components  
- Virtualization Tool: Oracle VM VirtualBox
- Domain Controller OS: Windows Server 2019
- Client Machine OS: Windows 10 Pro

---

## Configuration Steps  

### 1. Setting Up the Domain Controller (DC) VM
I started by creating a VM in VirtualBox for the Domain Controller:
- **Allocated Resources**:  
  - 4 GB of RAM  
  - 4 CPU cores  
- **Network Setup**:  
  - Added two network adapters:  
    1. One for internet access  
    2. Another for internal communication between VMs  
- **Operating System**
    - Mounted the Windows Server 2019 ISO to install the OS.
 
![DC](https://github.com/user-attachments/assets/b7ccd5a1-734d-4334-b83f-8982fbab3861)

To optimize the VM, I also installed **Guest Additions**.


### 2. Configuring the Internal Network
For internal communication between the VMs, I assigned a static IP address to the internal network adapter on the Domain Controller.
  - Renamed the network adapters for clarity:  
    - Internet adapter  
    - Internal network adapter
      
![dcnetwork](https://github.com/user-attachments/assets/555b3f05-d04a-4bdd-8f43-9b2631641b1d)


### 3. Setting Up Active Directory Domain Services (ADDS)
To set up Active Directory, I followed these steps:
- Opened Server Manager and selected Add Roles and Features.
- Chose the Active Directory Domain Services role and completed the installation.
- Promoted the server to a domain controller
- Created a new forest with the root domain name `paul-jang.com`

![ADDC](https://github.com/user-attachments/assets/eb34552b-19be-4cb1-bb71-03c520da339a)
- Created a New OU (Organizational Unit) called "_ADMINS" to store my admin account 
- Added a dedicated admin account:  
  - **Username**: `********`  
  - **Group Membership**: Domain_Admins
    


![a-pjangdc](https://github.com/user-attachments/assets/70856924-ec3e-48b4-b899-f624dec6e6ce)


### 4. Setting Up Remote Access (RAS/NAT)
To enable internet access for the internal network:
- Opened **Routing and Remote Access** in the server tools
- Configured NAT (Network Address Translation) to allow the client machine on the internal network to connect to the internet using the external-facing network adapter on the Domain Controller.

![RAS](https://github.com/user-attachments/assets/97fbcc82-4026-4d92-ad1a-b1f2bfe55e51)

### 5. Configuring DHCP
I installed and configured DHCP to automatically assign IP addresses to client machines:
- Created a new IPv4 scope
- Authorized the DHCP server using the domain name `dc.paul-jang.com`
- Refreshed the IPv4 configuration to ensure it was active
  
![dhcpdc](https://github.com/user-attachments/assets/f29f1a79-81a7-4e25-8edc-9bf418d1f65d)


### 6. Automate User Account Creation  
I wrote a script to generate 1,000 user accounts. Here's how I set it up in PowerShell ISE:
  1. Set the execution policy to unrestricted:  
     ```powershell
     Set-ExecutionPolicy Unrestricted
     ```  
  2. Navigated to the folder containing the script and the names file.  
  3. Ran the script to generate user accounts.  

![psdc](https://github.com/user-attachments/assets/ef81b0a3-42aa-42f3-8ce0-51e42935b6ca)

### 7. Creating a Client Machine
I set up a second VM for the client machine:
- Created `CLIENT1` using a Windows 10 Pro ISO.  
- **Network Configuration**: Set the network adapter to the internal network.  
- Renamed the PC to `CLIENT1`.  
- Joined the domain: `mydomain.com`.
  
![domain](https://github.com/user-attachments/assets/73b218d3-d0a6-46e2-b321-0e404c476be2)


### 8. Testing the Setup 
Finally, I verified the setup by logging into CLIENT1 with various domain user accounts to ensure everything was working as expected.
I am able to connect to the internet on the client machine using NAT and the Domain Controller acting as the default gateway.

![yoyu](https://github.com/user-attachments/assets/dbc1fd88-4803-425c-a6d5-84469d65b037)

---

## Outcome  
The homelab is now fully operational, featuring a Domain Controller, DHCP, NAT, and automated user account management. This project has provided me with a solid foundation for experimenting with networking and domain administration, and I’m excited to keep building on it.
