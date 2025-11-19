# Standard Operation Procedure
## Setup of Virtual Linux server for Web Application Testing
**Company Name** - *MITT*\
**Address** - *130 Henlow Bay,Winnipeg,MB*\
**Department Number** - *9876543210*

### Reversion info:
| Version | Date | Author | Description |
|---------|------|------|------------|
| 1.0 | 19-11-2025 | Navroj Sekhon | Initial Release |

### Approved Table:
| Name | Role | Approval Date |
|------|------|----------------|
| Oggy | System Administrator | 2025-11-15 |
| Tom | IT Manager | 2025-11-16 |
| Jerry | Director of Technology | 2025-11-10 |

### Purpose:
This SOP outlines the standardized procedure for creating, configuring, and preparing a virtual Linux server suitable for web application testing in a controlled environment.
### Scope:
This SOP applies to IT students, junior system administrators, and lab personnel responsible for creating Linux virtual machines for development or pre-production testing.
### Accountability Matrix:
| Position | Task | 
|------|-------------|
| System Administrator | Install and configure virtual server| 
| Test Engineer | Deploy and test the web application on the server | 
| Supervisor | Review and approve final setup | 
### Definitions:
- **VM:** Virtual Machine  
- **LAMP Stack:** Linux, Apache, MySQL/MariaDB, PHP  
- **NAT Networking:** Virtual network mode allowing outbound internet access through the host.
- **UFW:** Uncomplicated Firewall – A built-in Linux firewall management tool.
- **Hypervisor:** Software that runs and manages virtual machines
### Procedure Steps:
#### Step 1: Pre-Configuration Requirements
- A computer with virtualization support (Intel VT-x / AMD-V).
- Virtualization software (choose one):
    - VMware Workstation Player
     - Oracle VirtualBox
     -  Hyper-V
- Linux ISO file (recommended: Ubuntu Server 22.04 LTS).
- Stable internet connection.
#### Step 2: Create the Virtual Machine
- Open VMware.
- Click Create New VM.
- Name the VM: web-test-server.
- Select Linux → Ubuntu (64-bit).
#### Step 3: Allocate Resources
Recommended minimum resources:
- CPU: 2 vCPUs
- RAM: 2–4 GB
- Storage: 20–40 GB (VDI or VMDK, dynamically allocated)
- Network Adapter:
     - NAT (for internet access)
     - Bridged (if other devices need access)
#### Step 4: Install Required Web Testing Software
Under Storage, attach the downloaded ISO file as a virtual optical disk.
#### Step 5: Linux Installation
1. Start VM and install Ubuntu server
2. Choose language and keyboard layout
3. Set hostname :- Tester
4. Create Admin User:
   - Username:User1
   - Password any
5.  Configure timezone.
6.  Select Use Entire Disk and then Auto Partitioning in Disk Partition page
7.  On network configuration page choose DHCP as it is easier.
8.  Select Install OpenSSH Server. It should be enabled.
9.  Complete the installation.
10. Reboot the VM














1. Open a browser and enter the server’s IP address.
 - You should see the Apache default page.
2. Test PHP:
   ```bash
   php -v
   ```
3. Validate MYSQL is running:
   ```bash
   sudo mysql -u root -e "SHOW DATABASES;"
   ```
4. Confirm the server can clone git repositories:
   ```bash
   git clone https://github.com/example/test-app.git
   ```
5. Document IP, login credentials, and environment notes.

### Reference or Related Documents:
- Ubuntu Server Documentation
- Apache HTTP Server Guide
- VMware User Documentation
- LAMP Stack Best Practices Guide
   
