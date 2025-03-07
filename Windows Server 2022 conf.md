# Configuration to Apply on ADDC01

## System Configuration

1. **Change the Machine Name**
   - Set the name of the machine to `ADDC01`

2. **Install Splunk Forwarder**

3. **Install and Configure Sysmon**
   - Install Sysmon and apply the configuration file

4. **Configure Splunk Forwarder**
   - Forward specific data by modifying the `inputs.conf` file

5. **Restart the Splunk Service**

6. **Configure Splunk to Receive Data**
   - Ensure Splunk is set up to receive data from this server

**Note:** These configurations are the same as those applied on the **Target-PC**.

---

# Active Directory Domain Services (AD DS) Setup

## 1. Install Active Directory Domain Services (AD DS)
AD DS is a Microsoft server role that manages and stores information about users, devices, and services on a network.

### How AD DS Works:
- Stores information in a **hierarchical structure**
- Authenticates users before they can access network resources
- Controls access to directory resources
- Uses **Domain Name System (DNS)** to help clients find domain controllers

### Installation Steps:
- Open **Server Manager**
- Click **Add Roles and Features** (Ensure to select **Role-based or Feature-based Installation**)
- Click **Next**, then select **Active Directory Domain Services**
- Click **Add Features**, then proceed with **Next** until installation completes

---

## 2. Promote the Server to a Domain Controller

- Click on the **Flag (Notification)** icon
- Select **Promote this server to a domain controller**
- Choose **Add a new forest**
- Provide the **Root Domain Name** (e.g., `myAD.local`)
- Click **Next**, set a **Directory Services Restore Mode (DSRM) password** (e.g., `ActiveDirectory2`), and continue until installation is complete
- The server will **restart** automatically after installation

---

## 3. Create Users for the New Domain

### Steps to Create Users:
- Go to **Tools -> Active Directory Users and Computers**
- The **Builtin** folder contains different security groups
- The **Users** folder contains the domain users

### Creating an Organizational Unit (OU):
- Click on **Domain -> New -> Organizational Unit**
- Enter the **OU name** (e.g., IT, Sales) and click **OK**

### Creating Users:
- Inside the **Organizational Unit**, right-click and select **New -> User**
- Fill out the form to create a user

### Example Users:
- **IT Department**:
  - **User:** Bianca Express
  - **Username:** `wara`
  - **Password:** `Warr12@`
- **HR Department**:
  - **User:** Tinashe Silas
  - **Username:** `tinashe`
  - **Password:** `tin123@`

---
