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

![image](https://github.com/user-attachments/assets/5b1f4dd7-7f12-4cdb-a7d1-933c4d82ef31)

![image](https://github.com/user-attachments/assets/487a35ab-0642-4203-ac67-724d95f54236)

   - Control Panel → Programs → Turn Windows features on or off
   - Enable:
     - ✔ Internet Information Services
     - ✔ World Wide Web Services → Application Development Features → ✔ CGI

2. **Install Required Tools**
   - `PHPManagerForIIS_V1.5.0.msi`
   - `rewrite_amd64_en-US.msi`
   - `VC_redist.x86.exe`

3. **Set Up PHP**
 ![image](https://github.com/user-attachments/assets/3ca2c226-d6b5-4a3c-8014-5dab74da9419)
 ![image](https://github.com/user-attachments/assets/900b5ca4-6c6d-434b-a6c0-5eda2138c9fb)


   - Create directory: `C:\PHP`
   - Extract `php-7.3.8-nts-Win32-VC15-x86.zip` to `C:\PHP`
   - Register PHP in IIS:
     - Open IIS Manager → PHP Manager → Register new PHP version → `C:\PHP\php-cgi.exe`

4. **Install MySQL 5.5.62**
5. ![image](https://github.com/user-attachments/assets/a404daa4-89be-4bda-b1c7-06be82da6deb)

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
4. 
![image](https://github.com/user-attachments/assets/ba79752b-d7a4-4414-a938-a547072abdcc)

   - Open IIS Manager → PHP Manager → Enable/Disable Extensions
   - Enable:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`

4. **Configure osTicket**
5. ![image](https://github.com/user-attachments/assets/19bae664-9f13-4d35-8f73-3a730316a6b7)

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
![image](https://github.com/user-attachments/assets/91143d15-dcd3-44dc-b717-2bc2c3f1a2ab)

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





- ✅ IIS with PHP registered
- ✅ osTicket setup screen
- ✅ Admin dashboard with SLAs and Help Topics
- ✅ Ticket submission page

```markdown
![IIS PHP Registration](./assets/iis-php.png)
![osTicket Admin Panel](./assets/admin-panel.png)
