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






<h2>Configuration Steps</h2>

![image](https://github.com/user-attachments/assets/ba0a9b02-3855-4793-9821-e946e6e27d95)
![image](https://github.com/user-attachments/assets/36c7b3e1-dcca-46c0-83e3-abdadba4bf6e)
![image](https://github.com/user-attachments/assets/bc7fde34-39b1-4448-8573-f10960ea6790)




<p>




### 🛡️ Configure Roles, Departments, and Teams

1. **Set Up Roles**
   *Purpose:* Group agents by permission level.

   * Navigate to: `Admin Panel → Agents → Roles`
   * Example: `Supreme Admin`

2. **Create Departments**
   *Purpose:* Control ticket visibility by function.

   * Navigate to: `Admin Panel → Agents → Departments`
   * Example: `SysAdmins` (separate from Help Desk or Networking)

3. **Build Teams**
   *Purpose:* Group agents across departments for specific workflows.

   * Navigate to: `Admin Panel → Agents → Teams`
   * Example: `Online Banking` team (includes agents from multiple departments)






</p>


![image](https://github.com/user-attachments/assets/7efd2689-4f94-4e5f-ba7f-6f41316e8ec7)



<p>



### ✉️ Control Ticket Submission Settings

* Go to: `Admin Panel → Settings → User Settings`
* **Allow Anyone to Create Tickets:**

  * **Uncheck**: *Require registration and login to create tickets*
  * This enables **unregistered users** to submit tickets through the support portal.

> ✅ Useful for public-facing help desks that don’t require user accounts.




</p>
<br />

![image](https://github.com/user-attachments/assets/64e0f630-20bf-4acd-9d97-ace60375e313)



<p>


---

### 👥 Add Support Agents

* Navigate to: `Admin Panel → Agents → Add New`
* Create agents and assign departments:

  * **Jane** → Department: `SysAdmins`
  * **John** → Department: `Support`

> Agents are the staff members who respond to tickets based on their assigned department and role.






</p>
<br />

![image](https://github.com/user-attachments/assets/74fea544-4918-4d04-bf71-cfd32c81a44d)


![image](https://github.com/user-attachments/assets/5b83a878-9102-4848-8d45-fe34a04bcb5d)



<p>



---

### ⏱️ Configure SLAs (Service Level Agreements)

* Go to: `Admin Panel → Manage → SLA`
* Define response time expectations:

  * **Sev-A** → Grace: `1 hour`, Schedule: `24/7`
  * **Sev-B** → Grace: `4 hours`, Schedule: `24/7`
  * **Sev-C** → Grace: `8 hours`, Schedule: `Business Hours`

> SLAs help prioritize ticket urgency and enforce response timelines.


![image](https://github.com/user-attachments/assets/f79cd2ac-7c2d-4b5f-9b31-43c3352368d8)



---

### 📝 Configure Help Topics

* Navigate to: `Admin Panel → Manage → Help Topics`
* Add common support categories to streamline ticket routing:

  * **Business Critical Outage**
  * **Personal Computer Issues**
  * **Equipment Request**
  * **Password Reset**
  * **Other**

> Help Topics guide users when submitting tickets and can trigger custom workflows or SLA assignments.





</p>
<br />
