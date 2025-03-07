# Configurations to Apply on a Target-PC

## 1. Set the PC Name
```bash
Target-PC
```

## 2. Configure Static IP Address
- **IP Address:** `192.168.1.100`
- **DNS Server:** `8.8.8.8`

## 3. Access Splunk Server from Target-PC
- Open a browser and navigate to:
  ```
  http://192.168.10.10:8000
  ```

## 4. Download and Install Splunk Universal Forwarder
- **Username:** `admin`
- **Forwarder IP Address:** `192.168.10.10` (Splunk Server)
- **Forwarder Port:** `9997`

## 5. Download Sysmon and Configuration File
- **Sysmon v15.14**
- **Sysmon Olaf Configuration File**
  - Open `Sysmonconfig.xml` from the first link
  - Save and download the file

## 6. Install Sysmon with the Configuration File
```bash
# Unzip Sysmon
# Open PowerShell and navigate to Sysmon's location
./Sysmon64.exe -i ../sysmonconfig.xml
```
- `-i` specifies the config file
- `../` refers to the parent directory where the config file is stored

## 7. Configure Splunk Forwarder to Send Data to Splunk Server
- Navigate to:
  ```
  C:\Program Files\SplunkUniversalForwarder\etc\system\default
  ```
- Locate `inputs.conf`
- Create a new `inputs.conf` file at:
  ```
  C:\Program Files\SplunkUniversalForwarder\etc\system\local
  ```
- Copy the content from GitHub and save it

## 8. Restart Splunk Forwarder and Change Log On Type
- Open **Services** as Administrator
- Search for **Splunk Forwarder**
- Double-click and go to **Log On**
  - If set to **Local System Account**, keep it unchanged
- Restart the service and check if **Sysmon** is running

## 9. Set Up Splunk to Receive Data from Target-PC
- Open a browser and navigate to:
  ```
  http://192.168.10.10:8000
  ```
- Log in with credentials
- **Create a new index:**
  - Go to `Settings -> Indexes`
  - Create a new index named **endpoint**
- **Enable Splunk Server to receive data:**
  - `Settings -> Forwarding and Receiving -> Receiving Data`
  - Click **New Receiving Port** and set **9997**

## 10. Test Splunk Data Reception
- In Splunk, go to **Search** and run:
  ```
  index="endpoint"
  ```
- Check **Host** → It should show `Target-PC`
- Check **Source** → It should list different source types

---

# Join Target-PC to the Windows Server Domain (myAD.local)

## 1. Attempt to Join Domain
- `PC -> Properties -> Advanced System Settings -> Group Name -> Change`
- Select **Domain** and try to join `myAD.local`
- This will fail because the DNS is not set properly

## 2. Configure DNS to Point to Windows Server
- **Network and Internet Adapter -> Change Adapter Options**
- Right-click **IPv4 -> Properties**
- Change **DNS Server** to:
  ```
  192.168.10.7
  ```
- Click **OK**

## 3. Verify Configuration
- Open **CMD** and type:
  ```bash
  ipconfig /all
  ```

---

# Set Up Remote Access to Target-PC

## 1. Enable Remote Desktop
- `PC -> Properties -> Advanced Settings (Administrator Access)`
- **Remote** → Select **Allow remote connection to this PC**
- **Select Users** → Click **Add**
  - Add users: `bianca, tinashe`

---
