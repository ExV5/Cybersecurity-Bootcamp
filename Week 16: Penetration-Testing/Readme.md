## Week 16 Homework Submission File: Penetration Testing 1

#### Step 1: Google Dorking


- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is:

  Karl Fitzgerald

- How can this information be helpful to an attacker:

  Information could be used for creating phishing or spearheading


#### Step 2: DNS and Domain Discovery

Enter the IP address for `demo.testfire.net` into Domain Dossier and answer the following questions based on the results:

    1. Where is the company located: Sunnyvale, CA 24085 
    2. What is the NetRange IP address: 65.61.137.64 - 65.61.137.127
    3. What is the company they use to store their infrastructure: Rackspace Backbone Engineering 
    4. What is the IP address of the DNS server: 65.61.137.117

#### Step 3: Shodan

- What open ports and running services did Shodan find: 

  80, 443, 8080. 

  Apache Tomcat/Coyote JSP engine

#### Step 4: Recon-ng

- Install the Recon module `xssed`. 
- Set the source to `demo.testfire.net`. 
- Run the module. 

Is Altoro Mutual vulnerable to XSS: Yes

### Step 5: Zenmap

Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:

- Command for Zenmap to run a service scan against the Metasploitable machine:
  - nmap -sV 192.168.0.10
- Bonus command to output results into a new text file named `zenmapscan.txt`:
  - nmap -sV -oN zenmapscan.txt 192.168.0.10
- Zenmap vulnerability script command:
  -  nmap --script smb-enum-shares 192.168.0.10
- Once you have identified this vulnerability, answer the following questions for your client:
  1. What is the vulnerability: This NSE scirpt attempts to list shares using the srvsvc.NetShareEnumAll MSRPC function and retrieve more information about them using srvsvc.NetShareGetInfo. If access to those functions is denied, a list of common share names are checked.

  2. Why is it dangerous: An attacker may be able to leverage this to read (and possibly write) files on remote hosts

  3. What mitigation strategies can you recommendations for the client to protect their server: Restrict access, cur inbound SMB access at corporate firewalls, apply security patches

---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.  
