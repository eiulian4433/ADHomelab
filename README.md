# ADHomelab
Active Directory Homelab, DNS, DHCP, GP, Etc
Active Directory Home Lab (VirtualBox)
# Active Directory Home Lab (VirtualBox)


Overview

In this project, I built a small corporate-style Active Directory environment using VirtualBox, Windows Server 2022, and Windows 10.
The goal of this lab was to practice core Windows Server administration and networking concepts commonly used in IT Support, Help Desk, and System Administration roles.

This lab includes:

•	- Active Directory Domain Services (AD DS)
•	- DNS
•	- DHCP
•	- NAT/Routing
•	- Domain-joined Windows client
•	- Bulk user creation with PowerShell
•	- Internal virtual networking
•	- Group policies


Lab Topology

<img width="1630" height="965" alt="lab" src="https://github.com/user-attachments/assets/ce9b0a6e-1933-4298-b815-00539c6382de" />


Technologies Used
•	- Oracle VirtualBox
•	- Windows Server 2022
•	- Windows 10 Pro
•	- Active Directory
•	- DHCP
•	- DNS
•	- PowerShell
•	- NAT / Routing and Remote Access


What I Configured

1. Instalation & download


I installed:

•	- Oracle VirtualBox
•	- VirtualBox Extension Pack

I downloaded:

•	- Windows Server 2022 ISO
•	- Windows 10 Pro ISO


2. Created the Domain Controller VM

I created a virtual machine named: winDC


<img width="1280" height="749" alt="vlcsnap-2026-05-12-22h29m07s126" src="https://github.com/user-attachments/assets/9d888dba-17c2-497a-b40a-44b765b92f86" />

Configuration:
•	- 4 GB RAM
•	- Multiple CPU cores
•	- 2 network adapters

Network adapters:
•	- NAT adapter for internet access
•	- Internal Network adapter for the private lab network

<img width="1271" height="742" alt="vlcsnap-2026-05-12-22h40m24s069" src="https://github.com/user-attachments/assets/4936672d-0288-4f9f-a794-dba913b4a7df" />

<img width="1270" height="736" alt="vlcsnap-2026-05-12-22h40m41s852" src="https://github.com/user-attachments/assets/3e8a4553-6a96-45c5-ad3a-9ef1ddc17f0a" />


3. Installed Windows Server 2022

<img width="1025" height="857" alt="vlcsnap-2026-05-12-22h45m17s479" src="https://github.com/user-attachments/assets/f6b777a3-f0c0-4c63-9a7d-d306948a61b7" />


I installed:

Windows Server 2022 Standard (Desktop Experience)

After installation:

•	- Set Administrator password

<img width="1026" height="857" alt="vlcsnap-2026-05-12-22h47m26s667" src="https://github.com/user-attachments/assets/4625859a-20b8-47b1-9040-a92c31c74f4c" />

•	- Installed VirtualBox Guest Additions
<img width="1026" height="853" alt="vlcsnap-2026-05-12-22h49m43s174" src="https://github.com/user-attachments/assets/912a6825-41c7-40e1-8ad5-6611d434d7b0" />
<img width="1011" height="853" alt="vlcsnap-2026-05-12-22h50m14s317" src="https://github.com/user-attachments/assets/49e09e68-c5a6-491a-8bb1-b77ccb5804e8" />

•	- Restarted the VM

<img width="1018" height="847" alt="vlcsnap-2026-05-12-22h50m41s797" src="https://github.com/user-attachments/assets/cd39af82-5820-4d90-a2d0-7ae50d03c2ba" />


4. Configured Networking

I renamed the network adapters for easier management:
•	- INTERNET
•	- INTERNAL

I configured a static IP address on the internal adapter:
IP Address: 172.16.0.1
Subnet Mask: 255.255.255.0
DNS Server: 127.0.0.1
I left the default gateway blank because the server itself would handle routing.


5. Installed Active Directory Domain Services

Using Server Manager, I installed:
Active Directory Domain Services (AD DS)
I promoted the server to a Domain Controller and created a new forest:
mydomain.com


6. Created Administrative Accounts

I created:
•	- A dedicated Organizational Unit (OU)
•	- A custom domain admin account
I added the account to:
Domain Admins
This allowed me to manage the domain using a separate admin account instead of the built-in Administrator account.


7. Configured NAT and Routing

I installed:
Remote Access
Then enabled:
•	- NAT
•	- Routing and Remote Access
This allowed internal client machines to access the internet through the Domain Controller.


8. Configured DHCP

I installed the DHCP role and configured a scope:
172.16.0.100 - 172.16.0.200
DHCP settings included:
•	- Default Gateway: 172.16.0.1
•	- DNS Server: 172.16.0.1
This allowed client machines to automatically receive:
•	- IP addresses
•	- DNS settings
•	- Gateway information


9. Bulk User Creation with PowerShell

I used a PowerShell script to automatically create over 1000 Active Directory users.
The script:
•	- Imported names from a text file
•	- Created usernames automatically
•	- Assigned passwords
•	- Added users into a dedicated OU
Example username format:
ienache
This helped me practice:
•	- PowerShell scripting
•	- Active Directory automation
•	- Bulk user management


10. Created Windows 10 Client VM

I created a second VM named: client

Configuration:
•	- Windows 10 Pro
•	- Internal Network adapter only

The client automatically received:
•	- An IP address from DHCP
•	- DNS settings
•	- Internet connectivity through NAT


11. Joined the Client to the Domain

I renamed the client machine: CLIENT1
Then joined it to:
mydomain.com
After restarting, I was able to log in using domain user accounts created earlier in Active Directory.
Example:
mydomain\ienache


12. Verification and Testing

I verified:
•	- DHCP leases
•	- DNS resolution
•	- Internet connectivity
•	- Domain authentication
•	- Domain-joined computer objects in Active Directory

Commands used:
ipconfig
ping google.com
ping mydomain.com
whoami


Skills Demonstrated

This project helped me practice and understand:

•	- Active Directory administration
•	- Windows Server installation and configuration
•	- DHCP configuration
•	- DNS configuration
•	- NAT and routing
•	- PowerShell scripting
•	- User and computer management
•	- Domain joining
•	- Virtual networking
•	- Troubleshooting Windows networking issues


Key Takeaways

Through this lab, I gained hands-on experience with how enterprise Windows environments function in real-world corporate networks.

I also learned:
•	- How centralized authentication works
•	- How domain users can log into multiple systems
•	- How DHCP and DNS interact in Active Directory environments
•	- How PowerShell can automate repetitive administrative tasks


Possible future additions:
•	- Group Policy Objects (GPOs)
•	- File shares and permissions
•	- WSUS
•	- VPN configuration
•	- SIEM integration
•	- Windows Server backups
•	- Additional client machines
•	- Security hardening

Conclusion

This project gave me practical experience with core IT infrastructure technologies commonly used in:

•	- Help Desk
•	- IT Support
•	- Junior System Administration
•	- Windows Enterprise environments

