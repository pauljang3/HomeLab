# Skills Learned from My Home Lab Project

Working on this home lab was a hands-on learning experience that helped me develop a solid foundation in IT infrastructure and troubleshooting. Here’s what I gained from this project:

---

## Active Directory Configuration

Setting up Active Directory was a huge milestone for me. I learned how to:  
- Install and configure Active Directory Domain Services (ADDS) on a Windows Server 2019 virtual machine.  
- Create and manage a new domain, including setting up Organizational Units (OUs) and creating user accounts.  
- Promote a server to a Domain Controller and configure it as the preferred DNS server to handle network requests.
  
![adddd](https://github.com/user-attachments/assets/afbc7a9f-91c0-4bb4-b113-d72d6715bc87)

What really stood out to me was how Active Directory acts as the backbone for managing resources and user access across the network. It made me realize how crucial it is to properly configure and maintain AD to ensure everything runs smoothly.

---

## Networking and Connectivity

I got hands-on experience with networking basics:  
- Set up DHCP to assign IP addresses automatically to client machines and configured NAT with Routing and Remote Access Services (RAS) to enable internet access.  
- Troubleshot DNS and network issues, like clients not connecting to the internet, by carefully reviewing configurations and testing settings.  

Using tools like `ping` and `ipconfig` made troubleshooting feel intuitive. It was rewarding to see how each adjustment brought everything closer to working seamlessly.

---

## Automating Tasks with PowerShell

PowerShell became one of my favorite tools during this project:  
- I wrote scripts to automate the creation of over 1,000 user accounts, saving hours of manual effort.  
- I also used it to test network configurations and ensure that everything was working as expected.

Learning how to script was a turning point for me. It taught me how I can use automation to streamline repetitive tasks, which is incredibly satisfying.

---

## Real-World Problem Solving

This project gave me a lot of practical troubleshooting experience. Here are a few examples:  
- I ran into an issue where my client machine wasn’t able to connect to the internet, even though the Domain Controller was set as the default gateway. Upon investigating, I found that the DNS settings on the Domain Controller were incorrect due to a typo in the IP address. After correcting the DNS IP address on the DC, the client machine was able to connect to the internet successfully.
- While setting up the DHCP server, I initially had issues with IP address assignments on the client machine. After checking the DHCP scope and authorization, I realized the DHCP server wasn’t properly authorized in Active Directory. Once I authorized it and refreshed the IPv4 settings, the client machine was able to obtain an IP address automatically, resolving the issue.
  
Each challenge felt like solving a puzzle, and I gained confidence with every fix.

---

## Key Takeaways

Building this home lab showed me how different parts of IT infrastructure work together. It helped me learn:  
- How to approach problems systematically and troubleshoot effectively.  
- How to configure and maintain core IT systems like Active Directory and DHCP.  
- The importance of testing every setup to make sure it works as expected.  

This project gave me a solid foundation and made me excited to keep building on these skills. I’m looking forward to applying what I’ve learned in real-world environments!
