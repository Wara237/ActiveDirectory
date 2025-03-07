# Splunk Server Configuration Guide

## 1. Change Dynamic IP to Static

Edit the network configuration file:
```bash
sudo nano /etc/netplan/00-installer-config.yaml
```
- Locate `dhcp: no`
- Add the following lines:
  ```yaml
  addresses: [192.168.10.10/24]  # Computer's static IP
  nameservers:
    addresses: [8.8.8.8]  # Google DNS
  routes:
    - to: default
      via: 192.168.10.1  # Default gateway
  ```

- Save the file and apply the changes:
  ```bash
  sudo netplan apply
  ```
- Verify the IP address:
  ```bash
  ip a
  ```
- Check internet connectivity:
  ```bash
  ping google.com
  ```

## 2. Download Splunk Free Trial
- Download the **Splunk Enterprise** for Linux (`.deb` package).

## 3. Install VirtualBox on Ubuntu (Splunk Server)
```bash
sudo apt-get install virtualbox
```

## 4. Configure Shared File
- Go to **Devices > Shared Folders**.
- Select the folder where you saved the Splunk free trial.
- Enable all options and click **OK**.
- Reboot the system:
  ```bash
  sudo reboot
  ```

## 5. Add User to VBoxsf Group
```bash
sudo adduser user vboxsf
```
If it fails, install VirtualBox Guest Utils and retry:
```bash
sudo apt-get install virtualbox-guest-utils
sudo reboot
```

## 6. Create a Shared Directory
```bash
mkdir share
```

## 7. Mount Shared File to the Directory
```bash
sudo mount -t vboxsf -o uid=1000,gid=1000 AD_Project share/
```

## 8. Extract Splunk Package
Navigate to the shared folder and install Splunk:
```bash
cd share
sudo dpkg -i splunk*.deb
```

## 9. Change User to Splunk
Navigate to the Splunk installation directory:
```bash
cd /opt/splunk
```
List files and check user/group ownership, then switch to the Splunk user:
```bash
sudo -u splunk bash
```

## 10. Install and Start Splunk
```bash
cd bin
./splunk start
```

## 11. Enable Splunk to Start on Boot
```bash
cd bin
sudo ./splunk enable boot-start -user splunk
```

---

### Notes
- Ensure you have the correct permissions before performing the setup.
- This guide is for educational and ethical use only.

---
