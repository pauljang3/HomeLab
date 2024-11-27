# Homelab Setup and Configuration  

## Objective  
To build a virtualized Active Directory environment using Oracle VM VirtualBox for experimenting with domain management, networking, and automation.

---

## Hardware Components  
- **Host Machine**: Spare PC with Intel i5, 16GB RAM, 500GB SSD  

---

## Software Components  
- **Virtualization Software**: Oracle VM VirtualBox  
- **Operating System for DC**: Windows Server 2019  
- **Operating System for Client**: Windows 10 Pro  

---

## Configuration Steps  

### 1. Create a Virtual Machine for the Domain Controller (DC)  
- **Resources Allocated**:  
  - 4 GB RAM  
  - 4 CPUs  

- **Network Adapters**:  
  1. Adapter 1: For Internet access  
  2. Adapter 2: For the VirtualBox internal network  

- **Additional Configuration**:  
  - Installed **Guest Additions**.  
  - Renamed network cards for clarity:  
    - Internet-facing adapter  
    - Internal network adapter  

### 2. Set Up Static IP for Internal Network  
- Configured a static IP for the internal network interface on the DC.  

### 3. Install and Configure Active Directory Domain Services (ADDS)  
- Promoted the server to a domain controller.  
- Created a new forest and named the root domain (e.g., `mydomain.com`).  
- Created an administrative account:  
  - **Username**: `********`  
  - **Group Membership**: Domain Admins  

### 4. Install and Configure Remote Access (RAS/NAT)  
- Opened **Routing and Remote Access** under **Tools**.  
- Configured NAT to allow internet access through one external IP.  

### 5. Set Up DHCP  
- Configured DHCP to assign IP addresses automatically to client machines:  
  - Created a new IPv4 scope.  
  - Authorized the DHCP server: `dc.mydomain.com`.  
  - Refreshed IPv4 settings.  

### 6. Adjust Local Server Settings  
- Disabled **Internet Explorer Enhanced Security** for easier management.  

### 7. Automate User Account Creation  
- Created a script to generate 1,000 user accounts:  
  1. Set the execution policy to unrestricted:  
     ```powershell
     Set-ExecutionPolicy Unrestricted
     ```  
  2. Navigated to the folder containing the script and the names file.  
  3. Ran the script to generate user accounts.  

### 8. Set Up a Client Machine  
- Created `CLIENT1` using a Windows 10 Pro ISO.  
- **Network Configuration**: Set the network adapter to the internal network.  
- Renamed the PC to `CLIENT1`.  
- Joined the domain: `mydomain.com`.  

### 9. Verify Client-Server Integration  
- Verified that all domain users could log in to `CLIENT1`.  

---

## Outcome  
Successfully configured a homelab environment with a functional domain controller, DHCP, NAT, and automated user account creation. This setup provides a platform for testing and learning about Active Directory, networking, and administrative automation.
