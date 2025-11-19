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
This SOP provides step-by-step procedures to deploy and configure a virtual Linux server intended for web application testing in a development environment. This ensures consistency, reliability, and repeatability across all deployments.
### Scope:
This SOP applies to IT students, junior system administrators, and lab personnel responsible for creating Linux virtual machines for development or pre-production testing.
### Accountability Matrix:
| Task | Responsible | Reviewer | Approver |
|------|-------------|----------|----------|
| VM Creation | System Administrator | IT Instructor | IT Manager |
| OS Installation | System Administrator | IT Instructor | IT Manager |
| Software Stack Setup | System Administrator | QA Team | IT Manager |
| Documentation | Student/Author | Instructor | Department Lead |
### Definitions:
**VM:** Virtual Machine  
A software-based computer running inside a hypervisor.

**LAMP Stack:** Linux, Apache, MySQL/MariaDB, PHP  
A common software stack used to host web applications.

**NAT Networking:** Virtual network mode allowing outbound internet access through the host.

**UFW:** Uncomplicated Firewall – A built-in Linux firewall management tool.
### Procedure Steps:
#### Step 1: Pre-Configuration Requirements
1. Download **Ubuntu Server 22.04 LTS ISO** from the official site.  
2. Ensure host system supports virtualization (Intel VT-x or AMD-V enabled).
3. Recommended VM resources:  
   - **2 vCPU**  
   - **4 GB RAM**  
   - **25–30 GB virtual disk**  
4. Select network mode: **NAT** (default) or **Bridged** (for LAN access).  
5. Verify the hypervisor is installed (VirtualBox or VMware Workstation).
#### Step 2: Create the Virtual Machine
1. Open the hypervisor and select **Create New Virtual Machine**.  
2. Choose:  
   - **OS Type:** Linux  
   - **Version:** Ubuntu (64-bit)  
3. Name the VM: **web-test-server**  
4. Allocate system resources according to requirements.  
5. Attach the Ubuntu ISO under the virtual optical drive.  
6. Create a new virtual disk (VDI/VMDK) with at least **25 GB** storage.
#### Step 3: Install the Linux Operating System
1. Boot the virtual machine with the ISO attached.  
2. Select **Install Ubuntu Server**.  
3. Configure:  
   - Time zone  
   - Keyboard  
   - User credentials  
   - Hostname: `web-test-server`  
4. Choose **guided storage** for automatic partitioning.  
5. Configure networking:  
   - Default: DHCP  
   - Optional: Static IP for testing environments  
6. Complete installation and reboot when prompted.
#### Step 4: Install Required Web Testing Software
After login, update the server using this command:

```bash
sudo apt update && sudo apt upgrade -y
```
After this, install essential packages:

```bash
sudo apt install apache2 php mariadb-server php-mysql git unzip ufw -y
After this step, enable and configure firewall:
```
```bash
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
```
Also, verify services:

```bash
systemctl status apache2
systemctl status mariadb
```
#### Step 5: Post-Setup Verification:
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
   
