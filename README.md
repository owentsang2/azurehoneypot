# azurehoneypot
This project involved deploying a honeypot on a Microsoft Azure virtual machine to observe and analyse unauthorised login attempts against an exposed service.

The purpose of the project was to investigate:

1. How quickly an exposed service receives login attempts
2. The volume of attempted attacks over time
3. The geographical origin of observed IP addresses
4. Which countries and cities generated the highest number of observed attempts
5. How honeypot data can be processed and visualised

The project was conducted as a controlled security experiment using infrastructure that I owned and configured for this purpose.

Architecture

The experiment consisted of:

Microsoft Azure virtual machine
Internet-facing network interface
Firewall configuration allowing the monitored service
Honeypot/logging system
Event collection
IP geolocation
Python-based data analysis
Geographic visualisation
Internet
    │
    ▼
Azure Virtual Machine
    │
    ├── Exposed service
    │
    ▼
Honeypot / Event Logging
    │
    ▼
Authentication Attempts
    │
    ▼
IP Addresses
    │
    ▼
Geolocation Data
    │
    ▼
Python Analysis
    │
    ├── Country frequency
    ├── City frequency
    └── Geographic map
Methodology

Created a resource group on Microsoft Azure.

Created a virtual network within the lab then a virtual machine that is able to use the netowkr.

Opened both the firewall on the network security group and also within the virtual machine by connecting to it via remote desktop.

Created a log analytics workspace to log all the security events.

Used Microsft Sentinel (SIEM) and installed Window Security Events to be able to capture the events.

Let the virtual network run for over 24 hours and captured over 5000 security events.

Using KQL query to sort process and clean the data.

Created a workbook in Microsft Defender to display the data in a geo location heatmap for analysis

Results

The collected events demonstrated repeated attempts to access the exposed service.

The data was grouped by geographical location to determine where the observed connection attempts originated.

Geographic Distribution




Attempts by Country




Attempts by City




Findings

The analysis identified differences in the number of observed attempts associated with different geographical locations.

The location with the highest number of observed events was:

<img width="450" height="341" alt="image" src="https://github.com/user-attachments/assets/a880091d-9f84-49dc-9a0c-373f68d9e44a" />


The country with the highest number of observed events was:

<img width="429" height="196" alt="image" src="https://github.com/user-attachments/assets/3e1b0549-c088-4097-8532-ee65ef4ceef5" />

The total number of recorded events was:

<img width="667" height="303" alt="image" src="https://github.com/user-attachments/assets/c0bd265d-18fb-4f52-a524-d9b64a7762bf" />

Important Limitations

The geographical locations should not be interpreted as the physical locations of the attackers.

IP geolocation databases generally identify the approximate location associated with an IP address. An IP address may belong to a VPN, proxy, cloud provider, compromised machine, hosting provider or other intermediary.

Therefore, the results represent the geographical distribution of the observed source IP addresses, rather than confirmed attacker locations.

Security Considerations

The honeypot was intentionally exposed for the purposes of the experiment. This creates security risks if the system is not properly isolated and monitored.

The experiment therefore required consideration of:

- Network isolation
- Firewall configuration
- Credentials
- System monitoring
- Data collection
- Secure removal of the test environment
- Skills Demonstrated
- -Microsoft Azure
- Cloud infrastructure
- Network security
- Honeypot deployment
- Log analysis
- Data processing
- IP geolocation
- Data visualisation
- Security monitoring
- Cybersecurity research
- Future Improvements

Possible extensions to the project include:

- Analysing attempted usernames
- Analysing password patterns without retaining sensitive credentials
- Measuring attacks over time
- Identifying repeated source IP addresses
- Comparing attack rates between exposed services
- Adding automated dashboards
- Integrating SIEM tools such as Microsoft Sentinel
- Creating alerts for unusual activity
- Comparing results across different time periods
