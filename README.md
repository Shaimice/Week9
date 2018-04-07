# Week 9 Project - Honeypot

Objective:  To create and execute basic honeypots and demonstrate their effectiveness at detecting and collecting data about the attacks. Low- and medium-interaction honeypots were used, allowing worms or attackers to interact with the system.  Interactions were then captured for analysis and data was captured in a json file.

Deployed Honeypots
- Honeypot-1 Dionaea with Http: used to detect shellcodes, supporting ipv6 and tls. Protocols include blackhole; epmap; ftp; http; memcache; mirror; mqtt; mssql; mysql; pptp; sip; smb; tftp; upnp.
- Honeypot-2 Shockpot Sinkhole: web application honeypot designed to find attackers attempting to exploit the Bash remote code vulnerability.
- Honeypot-3 ElasticHoney: simple elasticsearch honeypot designed to catch attackers exploiting remote code execution (RCE) vulnerabilities in elasticsearch
- Honeypot-4 Amun: python-based low-interaction honeypot, following the concepts of Nepenthes but extending it with more sophisticated emulation and easier maintenance.
- Honeypot-5 Snort: used as a simple sniffer or packet logger to monitor attacker activity and as an intrusion prevention system (IPS) to control outgoing packets from a honeypot/honeynet and nullify attacker attempts.
- Honeypot-6 Kippo: medium-interaction SSH honeypot written in Python and is used to log brute force attacks and the entire shell interaction performed by an attacker.

Issues
- Deployed the honeypots and checked on their status daily; however, on Day 4, when I attempted to log in to the virtual machine running Modern Honey Network (MHN), the response from the server was "504 Gateway Time Out nginx/1.4.6 (Ubuntu)".  After researching the error, the troubleshooting revealed the problem being significant network traffic which caused the timeout.  Chose a different location, network to conduct my analysis.
- After reviewing resource allocation using the Google Cloud Console, the dashboard reported Honeypot-1 Dionaea with Http: Instance is overutilized. Consider switching to the machine type: g1-small (1 vCPU, 1.7 GB memory).  This update would require and additional subscription fee, but the features that Google provides in the console are extremely informative.
- Attempting to retrieve the json records via GPC using the following command PS C:\> gcloud compute ssh mhn-admin --command="mongoexport --db mnemosyne --collection session > session.json", the command errored with the following output
  ERROR: (gcloud.compute.ssh) unrecognized arguments:
    --db mnemosyne
    --collection (did you mean '--project'?)  session
  -- Ran mongoexport directly within the virtual machine and then retrieved the file using gcloud compute scp mhn-admin through the Powershell on the local machine.

Summary of Data Collected
- Real-time Attack Locater: ![](https://github.com/Shaimice/Week9/blob/master/Map.gif)

- Number of Attacks
  -- Honeypot-1 Dionaea               7,624
  -- Honeypot-2 Shockpot Sinkhole        36
  -- Honeypot-3 ElasticHoney              9
  -- Honeypot-4 Amun                  8,969
  -- Honeypot-5 Snort                 1,917
  -- Honeypot-6 Kippo                 1,039

- Real-time Attack Locater: ![](https://github.com/Shaimice/Week9/blob/master/Map.gif)

- Attack Statistics: ![](https://github.com/Shaimice/Week9/blob/master/Honeypots/Slide5.jpeg)
- Top Passwords: ![](https://github.com/Shaimice/Week9/blob/master/Honeypot/Slide1.jpeg)
- Top User Name: ![](https://github.com/Shaimice/Week9/blob/master/Honeypots/Slide2.jpeg)
- Top User Name/Password: ![](https://github.com/Shaimice/Week9/blob/master/Honeypots/Slide3.jpeg)
- Top Attackers: ![](https://github.com/Shaimice/Week9/blob/master/Honeypots/Slide4.jpeg)

- Number of Malware Samples:  None achieved during collection period

- Unresolved Questions: None at this time.

Session.json: ![](https://github.com/Shaimice/Week9/blob/master/session.json)

Source:
- The Honeynet Project, https://www.honeynet.org/
