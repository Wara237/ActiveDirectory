# **Active Directory Security Monitoring and Brute Force Attack Detection**

## **Project Description**
This project focuses on configuring and securing an **Active Directory (AD) environment**, monitoring security events using **Splunk**, and simulating a **brute force attack** to analyze system responses. It involves setting up **Splunk Forwarders**, **Sysmon for event logging**, and configuring **Active Directory Domain Services (AD DS)**.

The project also includes an **attack simulation** on a target machine to detect unauthorized access attempts. After performing the attack, Splunk is used to analyze **failed login attempts (Event ID 4625)** and **successful logins (Event ID 4624)** to identify malicious activity. The goal is to enhance **incident response** and improve **network security monitoring** practices.

## **Key Features**
- **Active Directory Setup:** Configuring AD DS, creating users, and setting up organizational units.  
- **Security Monitoring with Splunk:** Implementing **Splunk Universal Forwarders** to collect and analyze logs.  
- **Sysmon Integration:** Enhancing event logging and tracking system activities.  
- **Brute Force Attack Simulation:** Performing an RDP brute force attack to test security defenses.  
- **Log Analysis:** Using Splunk queries to detect failed and successful login attempts, identifying attacker details.  

## **Objective**
The main objective of this project is to demonstrate **real-world security monitoring** techniques, detect unauthorized access, and improve **incident response** in an enterprise environment.

## **Future Improvements & Perspectives**
- **Automated Threat Detection:** Implementing **SIEM (Security Information and Event Management)** rules in Splunk to automatically flag suspicious activities.  
- **Real-time Alerts:** Setting up **email or SMS alerts** when a brute force attack is detected.  
- **Machine Learning for Anomaly Detection:** Integrating **AI-driven threat detection models** to analyze behavioral patterns and detect sophisticated attacks.  
- **Integration with Endpoint Detection and Response (EDR):** Using tools like **Microsoft Defender for Endpoint** to enhance security monitoring.  
- **Incident Response Playbook:** Creating a standardized **incident response plan** to handle detected attacks efficiently.  
- **Cloud Security Monitoring:** Expanding the project to monitor **Azure AD or AWS IAM logs** for cloud-based environments.  
- **Expanding Attack Simulations:** Testing other attack vectors, such as **phishing, lateral movement, and privilege escalation**, to improve overall security posture.  

By implementing these improvements, the project can evolve into a **fully automated and intelligent security monitoring system** capable of **detecting and responding to cyber threats in real time**.
