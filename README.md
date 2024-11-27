# Homelab Setup and Configuration  

## Objective  
I set up a virtualized Active Directory environment using Oracle VM VirtualBox. The goal was to create a space where I could learn and experiment with domain management, networking, and automating administrative tasks.



---

## Hardware Components  
For this project, I used a spare PC with the following specs:

- Processor: Intel i5
- Memory: 16GB RAM
- Storage: 500GB SSD

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
  - Renamed the network adapters for clarity:  
    - Internet adapter  
    - Internal network adapter  

To optimize the VM, I also installed **Guest Additions**.

### 2. Configuring the Internal Network
For internal communication between the VMs, I assigned a static IP address to the internal network adapter on the Domain Controller.

### 3. Installing Active Directory Domain Services (ADDS)
I set up the Domain Controller as follows:
- Promoted the server to a domain controller
- Created a new forest with the root domain name `mydomain.com`
- Added a dedicated admin account:  
  - **Username**: `********`  
  - **Group Membership**: Domain Admins

### 4. Setting Up Remote Access (RAS/NAT)
To enable internet access for the internal network:
- Opened **Routing and Remote Access** in the server tools
- Configured NAT to share internet access via the external adapter

### 5. Configuring DHCP
I installed and configured DHCP to automatically assign IP addresses to client machines:
- Created a new IPv4 scope
- Authorized the DHCP server using the domain name `dc.mydomain.com`
- Refreshed the IPv4 configuration to ensure it was active


### 6. Automate User Account Creation  
I wrote a script to generate 1,000 user accounts. Here's how I set it up:
  1. Set the execution policy to unrestricted:  
     ```powershell
     Set-ExecutionPolicy Unrestricted
     ```  
  2. Navigated to the folder containing the script and the names file.  
  3. Ran the script to generate user accounts.  

### 8. Creating a Client Machine
I set up a second VM for the client machine:
- Created `CLIENT1` using a Windows 10 Pro ISO.  
- **Network Configuration**: Set the network adapter to the internal network.  
- Renamed the PC to `CLIENT1`.  
- Joined the domain: `mydomain.com`.  

### 9. Testing the Setup 
Finally, I verified the setup by logging into CLIENT1 with various domain user accounts to ensure everything was working as expected.

---

## Outcome  
The homelab is now fully operational, featuring a Domain Controller, DHCP, NAT, and automated user account management. This project has provided me with a solid foundation for experimenting with networking and domain administration, and I’m excited to keep building on it.
