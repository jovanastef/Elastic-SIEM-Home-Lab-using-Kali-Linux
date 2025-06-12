# Elastic SIEM Home Lab using Kali Linux

This project demonstrates how to set up a basic home lab environment using Elastic SIEM for security event monitoring and Kali Linux as the test environment for generating security events. The lab provides a hands-on opportunity to learn and practice security monitoring, incident detection, and alerting using Elastic's SIEM capabilities.

## Overview
In this guide, we will:

* Set up an Elastic Cloud account and install Elastic Defend on a Linux system (Kali Linux in this case, but it works on any Linux distribution).
* Use Nmap to simulate network scanning and generate security events.
* Create a dashboard to visualize the events in Elastic.
* Set up an alert to detect Nmap activity.
  
## Prerequisites
* **Elastic Cloud** account. You can sign up for a free trial on Elastic Cloud.
* A Linux-based system (preferably Kali Linux).
* Basic knowledge of command-line interface and Linux system administration.
  
## Step 1: Elastic Defend Installation

1. **Sign up** on Elastic Cloud and set up your Elastic instance.

2. **Install Elastic Defend** on your Linux machine. In this project, we used Kali Linux, but the steps apply to any Linux system.

     Execute the following commands to download and install the Elastic Agent:

bash   
```
curl -L -O https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-8.15.3-linux-x86_64.tar.gz
tar xzvf elastic-agent-8.15.3-linux-x86_64.tar.gz
cd elastic-agent-8.15.3-linux-x86_64
sudo ./elastic-agent install --url=https://your-fleet-server-url:443 --enrollment-token=your-enrollment-token
```
Replace your-fleet-server-url and your-enrollment-token with the appropriate values from your Elastic Cloud Fleet setup.

3. Once the Elastic Agent is installed, you should start receiving security event data in your Elastic dashboard.

## Step 2: Nmap Testing on Kali Linux

1. **Nmap** is a network scanning tool used to identify open ports and services on a network. On **Kali Linux***, it comes pre-installed. If you are using a different Linux distribution, you can install Nmap using the following command:

bash
```
sudo apt-get install nmap
```
2. Run Nmap commands to generate security events:

bash
```
nmap -sS localhost
nmap -sU localhost
```
These scans will trigger events in Elastic SIEM, which can be monitored and visualized.

## Step 3: Creating a Dashboard to Visualize Events
Once Elastic Defend is operational and Nmap scans are generating events, follow these steps to create a dashboard:

1. Go to the Elastic SIEM interface.
2. Navigate to Kibana -> Dashboards.
3. Create a new dashboard, selecting visualizations to monitor the incoming security events. You can add graphs, tables, and charts based on the data from your Nmap scans.

## Step 4: Setting Up an Nmap Alert

To detect and get alerted on Nmap activity:

1. In the Elastic SIEM interface, go to Kibana -> Security -> Alerts.
2. Create a new rule to detect Nmap activity based on the patterns of the network scans.
3. Set the alert to trigger whenever an Nmap scan is detected, and visualize the alert data on your dashboard.

![Capture](https://github.com/user-attachments/assets/34b0b0dc-ccb3-46f5-8df0-6b203cf8e218)

## Conclusion

This project demonstrates the essential steps to create a basic SIEM home lab using Elastic Defend and Kali Linux. By following these steps, you can gain valuable experience in:

* Security event monitoring.
* Dashboard creation for visualizing security events.
* Creating alerts to detect network scanning activities.
This lab provides a foundational environment for developing security analyst skills, including incident response and threat detection using Elastic SIEM.

## Next Steps
To extend this lab, consider:

* Adding more complex attack simulations using tools like Metasploit.
* Automating alerts and integrating with external systems like TheHive for incident response.
* Experimenting with different types of Beats agents to collect data from multiple sources.
***  
Feel free to adjust the URLs, tokens, and other values based on your actual setup! Let me know if you need further refinements or changes.
