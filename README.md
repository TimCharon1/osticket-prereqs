<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>



### ✅ Prerequisites for osTicket Installation


1. **Create a Windows 10 Azure VM**

   * 4 vCPUs, Name: `osticket-vm`
   * Username: `labuser`, Password: `osTicketPassword1!`

2. **Connect via Remote Desktop**

   * Log into the VM using the credentials above.

3. **Download & Unzip Files**

   * Extract `osTicket-Installation-Files.zip` to the desktop inside the VM.

4. **Install IIS with CGI Enabled**

   * Enable IIS via Windows Features → Application Development Features → ✅ CGI.

5. **Verify IIS is Running**

   * Visit `http://localhost` in a browser inside the VM.

6. **Access osTicket Panels**

   * **Admin/Agent Login:** `http://localhost/osTicket/scp/login.php`
   * **End User Portal:** `http://localhost/osTicket`

7. **Know the Difference**

   * **Agent Panel:** For staff managing tickets.
   * **Admin Panel:** For system settings (admins only).






<h2>Installation Steps</h2>

![image](https://github.com/user-attachments/assets/2da2fd98-4a52-4fe2-a7d7-3ceb5d2e4152)

<p>


### ⚙️ osTicket Manual Environment Setup (Windows + IIS)

To manually deploy **osTicket** on a Windows system using **IIS**, I performed the following steps:

1. **Installed PHP Manager for IIS**
   From `PHPManagerForIIS_V1.5.0.msi` to simplify PHP configuration in IIS.

2. **Installed IIS Rewrite Module**
   Using `rewrite_amd64_en-US.msi` to enable clean URL support for osTicket.

3. **Set Up PHP Directory**
   Created `C:\PHP` and extracted `php-7.3.8-nts-Win32-VC15-x86.zip` into it.

4. **Installed Visual C++ Redistributable**
   Ran `VC_redist.x86.exe` to support PHP runtime.

5. **Installed MySQL 5.5.62**
   Used `mysql-5.5.62-win32.msi` → Typical Setup → Standard Configuration via the MySQL Wizard.




</p>


![image](https://github.com/user-attachments/assets/eb39140a-b165-468c-843d-6bcecdd9e45c)


<p>


### 🛠️ Enabling Required PHP Extensions for osTicket

After installing PHP and launching osTicket in the browser, I received a warning indicating that some required PHP extensions were not enabled. To resolve this, I used **PHP Manager for IIS** to activate the necessary extensions:

1. Opened **IIS Manager**, navigated to:
   `Sites → Default Web Site → osTicket`

2. Double-clicked **PHP Manager** to access PHP configuration tools.

3. Selected **“Enable or disable an extension”** from the available options.

4. Manually enabled the following extensions:

   * `php_imap.dll` – Supports email fetching via IMAP.
   * `php_intl.dll` – Provides internationalization support.
   * `php_opcache.dll` – Improves PHP performance through opcode caching.

5. Refreshed the osTicket site in the browser to confirm that all required extensions were now enabled and the warning message was resolved.

This step was critical to ensuring full feature compatibility with osTicket, particularly email ticketing and localization features.



</p>
<br />

![image](https://github.com/user-attachments/assets/eaae4e86-7d3b-45c6-9a88-bad02d4c955b)


<p>


---

### 🧾 Final osTicket Configuration & Database Setup

#### 🔧 Rename Config File

Renamed the sample config file:

```
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php  
To:   C:\inetpub\wwwroot\osTicket\include\ost-config.php
```

#### 🔐 Set Permissions

* Disabled inheritance on `ost-config.php`
* Removed existing permissions
* Granted **Everyone** full control

#### 🌐 Complete Browser Setup

* Opened osTicket in the browser
* Clicked **Continue**
* Named the helpdesk and set a default support email

#### 🗃️ Create MySQL Database (HeidiSQL)

* Installed **HeidiSQL**
* Connected using `root/root`
* Created a new database: `osTicket`



</p>
<br />

![image](https://github.com/user-attachments/assets/0a485657-8a92-48ae-9978-8265592afa34)

![image](https://github.com/user-attachments/assets/849fba59-9eb0-4aa7-b1f9-6ac24452d4f3)


<p>


### 🚀 Finalizing osTicket Installation

* Continued the setup in the browser
* Entered the following MySQL details:

  * **Database:** `osTicket`
  * **Username:** `root`
  * **Password:** `***`
* Clicked **“Install Now!”** to complete installation

✅ If successful, the system confirms installation with no errors.

#### 🔑 Access URLs:

* **Admin Panel (Staff Login):**
  `http://localhost/osTicket/scp/login.php`

* **End User Support Portal:**
  `http://localhost/osTicket/`



</p>
<br />
