<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo" width="300"/>
</p>

# 🧰 osTicket - Prerequisites and Installation (Azure VM)

This project demonstrates the step-by-step deployment and configuration of the **osTicket** support ticketing system on a **Windows 10 Azure Virtual Machine**. The environment was manually set up to simulate a real-world deployment, complete with IIS, PHP, MySQL, and osTicket installation.

---

## 🌐 Environments and Technologies Used

- Microsoft Azure (Virtual Machines)
- Windows 10 (21H2)
- Remote Desktop Protocol (RDP)
- Internet Information Services (IIS)
- PHP 7.3.8 (Non-thread-safe)
- MySQL 5.5.62
- osTicket v1.15.8
- HeidiSQL

---

## ✅ Prerequisites for osTicket Installation
![image](https://github.com/user-attachments/assets/54ee7259-ced0-4919-b183-42d9b77b90c3)

1. **Create Azure Virtual Machine**
   - Windows 10, 4 vCPUs
   - Name: `osticket-vm`
   - Username: `labuser`
   - Password: `osTicketPassword1!`

2. **Remote into the VM**
   - Use RDP to log in with the credentials above

3. **Download & Unzip Files**
   - Place the `osTicket-Installation-Files.zip` on the VM Desktop
   - Extract to a folder named: `osTicket-Installation-Files`

---

## ⚙️ System Setup (Inside the VM)
![image](https://github.com/user-attachments/assets/d0644cc0-abba-4dc4-8335-6dda6ffb6a50)

1. **Enable IIS with CGI**
   - Control Panel → Programs → Turn Windows features on or off
   - Enable:
     - ✔ Internet Information Services
     - ✔ World Wide Web Services → Application Development Features → ✔ CGI

2. **Install Required Tools**
   - `PHPManagerForIIS_V1.5.0.msi`
   - `rewrite_amd64_en-US.msi`
   - `VC_redist.x86.exe`

3. **Set Up PHP**
   - Create directory: `C:\PHP`
   - Extract `php-7.3.8-nts-Win32-VC15-x86.zip` to `C:\PHP`
   - Register PHP in IIS:
     - Open IIS Manager → PHP Manager → Register new PHP version → `C:\PHP\php-cgi.exe`

4. **Install MySQL 5.5.62**
   - Typical Setup
   - Launch Configuration Wizard
   - Standard Configuration:
     - Username: `root`
     - Password: `root`

---

## 📁 osTicket Installation

1. **Extract osTicket Files**
   - From `osTicket-Installation-Files`, unzip `osTicket-v1.15.8.zip`
   - Copy the `upload` folder to: `C:\inetpub\wwwroot`
   - Rename `upload` to `osTicket`

2. **Restart IIS**
   - IIS Manager → Stop → Start

3. **Enable Required PHP Extensions**
4. ![image](https://github.com/user-attachments/assets/ba79752b-d7a4-4414-a938-a547072abdcc)

   - Open IIS Manager → PHP Manager → Enable/Disable Extensions
   - Enable:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`

5. **Configure osTicket**
   - Rename config file:
     - From: `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
     - To: `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
   - Set Permissions:
     - Disable inheritance
     - Remove all
     - Add `Everyone` with full control

---

## 🌐 Complete Installation in Browser
![image](https://github.com/user-attachments/assets/1afb3c36-acc6-4948-a6c4-1b21a4b80553)

1. **Visit osTicket in Browser**
   - Admin Panel: `http://localhost/osTicket/scp/login.php`
   - End User Portal: `http://localhost/osTicket`

2. **Complete Setup Wizard**
   - Helpdesk Name: *(e.g., YourCompany Helpdesk)*
   - Default Email: *(e.g., support@yourcompany.com)*
   - MySQL Settings:
     - DB Name: `osTicket`
     - User: `root`
     - Password: `root`

3. **Install Now**
   - Confirm no errors
   - Log in using the admin credentials created

---

## 🔒 Post-Install Cleanup

1. **Delete Setup Folder**
   - `C:\inetpub\wwwroot\osTicket\setup`

2. **Secure Config File**
   - Set `C:\inetpub\wwwroot\osTicket\include\ost-config.php` to **read-only**

---

## 👨‍💼 Configure osTicket for Use

### 🛡️ Create Roles, Departments, and Teams
![image](https://github.com/user-attachments/assets/b7d5be2d-c5ee-435e-bc31-98463554a6d9)
![image](https://github.com/user-attachments/assets/10c89470-1bb4-4dfa-a712-726521332f5c)
![image](https://github.com/user-attachments/assets/1980f17d-8712-423a-80a5-9d23cf6fe1f8)



- **Roles** (Admin Panel → Agents → Roles)
  - Example: `Supreme Admin`
- **Departments** (Admin Panel → Agents → Departments)
  - Example: `SysAdmins`, `Support`
- **Teams** (Admin Panel → Agents → Teams)
  - Example: `Online Banking`

### ✉️ Ticket Submission Settings

- Admin Panel → Settings → User Settings
- Uncheck: *Require registration and login to create tickets*

### 👥 Add Support Agents
![image](https://github.com/user-attachments/assets/aa918283-b6ca-47b3-a179-7c4202a85bf1)

- Admin Panel → Agents → Add New
  - `Jane` → Department: SysAdmins
  - `John` → Department: Support

### ⏱️ Define SLAs
![image](https://github.com/user-attachments/assets/35d0f03c-5618-45a1-8cee-1ceee0bc740d)


- Admin Panel → Manage → SLA
  - Sev-A → 1hr, 24/7
  - ![image](https://github.com/user-attachments/assets/96cf9675-0a05-4725-aaae-ebaec8ba0c6a)

  - Sev-B → 4hr, 24/7
  - ![image](https://github.com/user-attachments/assets/ccdffc0f-6def-4cfa-a4d7-10d6f495d262)

  - Sev-C → 8hr, Business Hours
  - ![image](https://github.com/user-attachments/assets/104a03d0-8abf-44db-909b-fc1a20bdf136)


### 📝 Add Help Topics
![image](https://github.com/user-attachments/assets/7892e6e8-2f5f-41b4-95d7-d38fb5b35be2)


- Admin Panel → Manage → Help Topics
  - Business Critical Outage
  - Personal Computer Issues
  - Equipment Request
  - Password Reset



- ✅ IIS with PHP registered
- ✅ osTicket setup screen
- ✅ Admin dashboard with SLAs and Help Topics
- ✅ Ticket submission page

```markdown
![IIS PHP Registration](./assets/iis-php.png)
![osTicket Admin Panel](./assets/admin-panel.png)
