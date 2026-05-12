# ADHomelab
Active Directory Homelab, DNS, DHCP, GP, Etc
Active Directory Home Lab (VirtualBox)
# Active Directory Home Lab (VirtualBox)
Overview
In this project, I built a small corporate-style Active Directory environment using VirtualBox, Windows Server 2022, and Windows 10. The goal of this lab was to practice core Windows Server administration and networking concepts commonly used in IT Support, Help Desk, and System Administration roles.
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
INTERNET
    |
[Windows Server 2022 Domain Controller]
    |
    |-- NAT / Routing
    |
[Internal Virtual Network]
    |
[Windows 10 Client]
Technologies Used
•	- Oracle VirtualBox
•	- Windows Server 2022
•	- Windows 10 Pro
•	- Active Directory
•	- DHCP
•	- DNS
•	- PowerShell
•	- NAT / Routing and Remote Access
•	
What I Configured
1. Installed VirtualBox
I installed:
•	- Oracle VirtualBox
•	- VirtualBox Extension Pack
I also downloaded:
•	- Windows Server 2022 ISO
•	- Windows 10 Pro ISO
2. Created the Domain Controller VM
I created a virtual machine named:
DC
Configuration:
•	- 4 GB RAM
•	- Multiple CPU cores
•	- 2 network adapters
Network adapters:
•	- NAT adapter for internet access
•	- Internal Network adapter for the private lab network
3. Installed Windows Server 2022
I installed:
Windows Server 2022 Standard (Desktop Experience)
After installation:
•	- Set Administrator password
•	- Installed VirtualBox Guest Additions
•	- Restarted the VM
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
jsmith
This helped me practice:
•	- PowerShell scripting
•	- Active Directory automation
•	- Bulk user management
10. Created Windows 10 Client VM
I created a second VM named:
CLIENT1
Configuration:
•	- Windows 10 Pro
•	- Internal Network adapter only
The client automatically received:
•	- An IP address from DHCP
•	- DNS settings
•	- Internet connectivity through NAT
11. Joined the Client to the Domain
I renamed the client machine:
CLIENT1
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
Future Improvements
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
It also served as a strong introduction to enterprise networking and Active Directory management in a safe lab environment.
