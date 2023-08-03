## Network Security Homework

Make a copy of this document to work in, and then fill out the solution for each prompt below. Save and submit this completed file as your Challenge deliverable.


### Part 1: Review Questions 


#### Security Control Types

The concept of defense in depth can be broken down into three security control types. Identify the security control type of each set of defense tactics.



1.  Walls, bollards, fences, guard dogs, cameras, and lighting are what type of security control?

```
Physical Controls
```


2. Security awareness programs, BYOD policies, and ethical hiring practices are what type of security control?

```
Administrative Controls
```


3. Encryption, biometric fingerprint readers, firewalls, endpoint security, and intrusion detection systems are what type of security control?

```
Technical Control
```




#### Intrusion Detection and Attack Indicators



1. What’s the difference between an IDS and an IPS?

```
There are several differences between these two types of systems. IDS only issues alerts for potential attacks, while IPS can take action against them. Also, IDS is not inline, so traffic doesn't have to flow through it. Traffic does, however, have to flow through your IPS. In addition, false positives for IDS will only cause alerts, while false positives for IPS could cause the loss of important data or functions (https://www.dnsstuff.com/ids-vs-ips).
```


2. What’s the difference between an indicator of attack (IOA) and an indicator of compromise (IOC)?

```
Indicators of attack (IOA) focus on detecting the intent of what an attacker is trying to accomplish, regardless of the malware or exploit used in an attack. 
An Indicator of Compromise (IOC) is often described in the forensics world as evidence on a computer that indicates that the security of the network has been breached. Investigators usually gather this data after being informed of a suspicious incident, on a scheduled basis, or after the discovery of unusual call-outs from the network. Ideally, this information is gathered to create "smarter" tools that can detect and quarantine suspicious files in the future.(https://www.crowdstrike.com/cybersecurity-101/indicators-of-compromise/ioa-vs-ioc/)

```




#### The Cyber Kill Chain

Name the seven stages of the cyber kill chain, and provide a brief example of each.



1. Stage 1: 

```
Reconnaissance
The observation stage: attackers typically assess the situation from the outside-in, in order to identify both targets and tactics for the attack.
```


2. Stage 2:

```
Weaponization
Attackers develop malware by leveraging security vulnerabilities. Attackers engineer malware based on their needs and the intention of the attack. This process also involves attackers trying to reduce the chances of getting detected by the security solutions that the organization has in place.
```


3. Stage 3:

```
Delivery
The attacker delivers the weaponized malware via a phishing email or some other medium. The most common delivery vectors for weaponized payloads include websites, removable disks, and emails. This is the most important stage where the attack can be stopped by the security teams. 
```


4. Stage 4:

```
Exploitation
The malicious code is delivered into the organization's system. The perimeter is breached here. And the attackers get the opportunity to exploit the organization's systems by installing tools, running scripts, and modifying security certificates. 
```


5. Stage 5:

```
Installation
A backdoor or remote access trojan is installed by the malware that provides access to the intruder. This is also another important stage where the attack can be stopped using systems such as HIPS (Host-based Intrusion Prevention System).
```


6. Stage 6:

```
Command and Control
The attacker gains control over the organization's systems and network. Attackers gain access to privileged accounts and attempt brute force attacks, search for credentials, and change permissions to take over the control..
```


7. Stage 7:

```
Actions on Objective
The attacker finally extracts the data from the system. The objective involves gathering, encrypting, and extracting confidential information from the organization's environment. 
```




```
Work Cited (https://www.computer.org/publications/tech-news/trends/what-is-the-cyber-kill-chain-and-how-it-can-protect-against-attacks)
```



#### Snort Rule Analysis

Use the provided Snort rules to answer the following questions:

**Snort Rule #1**


```
alert tcp $EXTERNAL_NET any -> $HOME_NET 5800:5820 (msg:"ET SCAN Potential VNC Scan 5800-5820"; flags:S,12; threshold: type both, track by_src, count 5, seconds 60; reference:url,doc.emergingthreats.net/2002910; classtype:attempted-recon; sid:2002910; rev:5; metadata:created_at 2010_07_30, updated_at 2010_07_30;)
```




1. Break down the Snort rule header and explain what this rule does.

```
The action that Snort will take when triggered is to Alert users. The rule applies to all incoming TCP packets from outside network EXTERNAL_NET (anywhere but HOME_NET) from ANY port going to protected network HOME_NET to destination ports 5800-5820.
```


2. What stage of the cyber kill chain does the alerted activity violate?

```
The first stage - Reconnaissance 
```


3. What kind of attack is indicated?

```
ET SCAN Potential VNC Scan 5800-5820
```



**Snort Rule #2**


```
alert tcp $EXTERNAL_NET $HTTP_PORTS -> $HOME_NET any (msg:"ET POLICY PE EXE or DLL Windows file download HTTP"; flow:established,to_client; flowbits:isnotset,ET.http.binary; flowbits:isnotset,ET.INFO.WindowsUpdate; file_data; content:"MZ"; within:2; byte_jump:4,58,relative,little; content:"PE|00 00|"; distance:-64; within:4; flowbits:set,ET.http.binary; metadata: former_category POLICY; reference:url,doc.emergingthreats.net/bin/view/Main/2018959; classtype:policy-violation; sid:2018959; rev:4; metadata:created_at 2014_08_19, updated_at 2017_02_01;)
```




1. Break down the Sort rule header and explain what this rule does.

```
This Snort rule creates an alert that applies to all TCP packets coming from any IP address from the external network through HTTP_PORT 80 to any ports on the home network.The "ET POLICY" part of the alert is telling that it's a 'Policy' rule: i.e. it's not an attack per se, it's just something which might violate a corporate policy.That particular alert is telling users that someone has downloaded a Windows executable file or DLL over HTTP. 
```


2. What layer of the defense in depth model does the alerted activity violate?

```
Host Layer 
```


3. What kind of attack is indicated?

```
Ransomware
```



**Snort Rule #3**

Your turn! Write a Snort rule that alerts when traffic is detected inbound on port `4444` to the local network on any port. Be sure to include the `msg` in the rule option.


```
alert tcp $EXTERNAL_NET 4444 -> $HOME_NET any (msg: "TCP packet Detected through port 4444";)
```



### Part 2: “Drop Zone” Lab


#### Set up.

Log in using the following credentials:



* Username: `sysadmin`
* Password: `cybersecurity`


#### Uninstall UFW.

Before getting started, you should verify that you do not have any instances of UFW running. This will avoid conflicts with your firewalld service. This also ensures that firewalld will be your default firewall.



* Run the command that removes any running instance of UFW.

```
sudo apt -y remove ufw
```




#### Enable and start firewalld.

By default, the firewalld service should be running. If not, then run the commands that enable and start firewalld upon boots and reboots.


```
sudo systemctl enable firewalld
sudo systemctl start firewalld
```



```
Note: This will ensure that firewalld remains active after each reboot.
```



#### Confirm that the service is running.

Run the command that checks whether the `firewalld` service is up and running.

  


```
sudo /etc/init.d/firewalld status
```



#### List all firewall rules currently configured.

Next, list all currently configured firewall rules. This will give you a good idea of what’s currently configured and save you time in the long run by ensuring that you don’t duplicate work that’s already done.



* Run the command that lists all currently configured firewall rules:

```
firewall-cmd –-list-all
```


![Screenshot 2023-08-03 101159](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/2e5daab2-41ab-4756-8fb3-9232597ff4aa)



* Take note of what zones and settings are configured. You may need to remove unneeded services and settings.


#### List all supported service types that can be enabled.



* Run the command that lists all currently supported services to find out whether the service you need is available.

```
sudo firewall-cmd --list-all 
```


* Notice that the `home` and `drop` zones are created by default.


#### Zone views.



* Run the command that lists all currently configured zones.

```
sudo firewall-cmd --list-all-zones
```


* Notice that the `public` and `drop` zones are created by default. Therefore, you will need to create zones for `web`, `sales`, and `mail`.


#### Create zones for `web`, `sales`, and `mail`.



* Run the commands that create `web`, `sales`, and `mail` zones.

```
sudo firewall-cmd --permanent --new-zone=web  
sudo firewall-cmd --permanent --new-zone=sales  
sudo firewall-cmd --permanent --new-zone=mail  
sudo firewall-cmd --reload  
sudo firewall-cmd --permanent --list-all-zones
```




#### Set the zones to their designated interfaces.



* Run the commands that set your `eth` interfaces to your zones.

```
sudo firewall-cmd --zone=public --change-interface=eth0  
sudo firewall-cmd --zone=web --change-interface=eth1  
sudo firewall-cmd --zone=sales --change-interface=eth2  
sudo firewall-cmd --zone=mail --change-interface=eth3 
```




#### Add services to the active zones.



* Run the commands that add services to the `public` zone, the `web` zone, the `sales` zone, and the `mail` zone.
* `public`:

```
sudo firewall-cmd --permanent --zone=public --add-service=http  
sudo firewall-cmd --permanent --zone=public --add-service=https  
sudo firewall-cmd --permanent --zone=public --add-service=pop3  
sudo firewall-cmd --permanent --zone=public --add-service=smtp
```


* `web`:

```
sudo firewall-cmd --permanent --zone=web --add-service=https 
sudo firewall-cmd --permanent --zone=web --add-service=http 
```


* `sales`:

```
sudo firewall-cmd --permanent --zone=sales --add-service=https
```


* `mail`:

```
sudo firewall-cmd --permanent --zone=mail --add-service=smtp  
sudo firewall-cmd --permanent --zone=mail --add-service=pop3
```


* What is the status of `http`, `https`, `smtp` and `pop3`?

![Screenshot 2023-08-03 101450](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/5670c791-2f02-47c4-a385-c2a3137299db)




#### Add your adversaries to the `drop` zone.



* Run the command that will add all current and any future blacklisted IPs to the `drop` zone.

```
sudo firewall-cmd --permanent --zone=drop --add-source=10.208.56.23  
sudo firewall-cmd --permanent --zone=drop --add-source=135.95.103.76  
sudo firewall-cmd --permanent --zone=drop --add-source=76.34.169.118
```




#### Make rules permanent, then reload them.

It's good practice to ensure that your firewalld installation remains nailed up and retains its services across reboots. This helps ensure that the network remains secure after unplanned outages such as power failures.



* Run the command that reloads the firewalld configurations and writes it to memory:

```
sudo firewall-cmd --runtime-to-permanent
```




#### View active zones.

Now, provide truncated listings of all currently **active** zones. This is a good time to verify your zone settings.



* Run the command that displays all zone services.

```
sudo firewall-cmd --get-active-zones
```


![Screenshot 2023-08-03 101529](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/0c04396f-ef3a-435c-a74a-e527d2588190)


#### Block an IP address.



* Use a rich-rule that blocks the IP address `138.138.0.3` on your `public` zone.

```
sudo firewall-cmd --zone=drop --add-rich-rule="rule family='ipv4' source address='138.138.0.3' reject"
```




#### Block ping/ICMP requests.

Harden your network against `ping` scans by blocking `icmp ehco` replies.



* Run the command that blocks `pings` and `icmp requests` in your `public` zone.

```
sudo firewall-cmd --zone=public --add-icmp-block=echo-reply --add-icmp-block=echo-request
```




#### Rule check.

Now that you've set up your brand new firewalld installation, it's time to verify that all of the settings have taken effect.



* Run the command that lists all of the rule settings. Do one command at a time for each zone.

```
sudo firewall-cmd --zone=public --list-all  
sudo firewall-cmd --zone=sales --list-all
sudo firewall-cmd --zone=mail --list-all
sudo firewall-cmd --zone=web --list-all
sudo firewall-cmd --permanent --zone=drop --list-all
```





![Screenshot 2023-08-03 101629](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/fd88fe89-b1f2-42b2-bfa0-c942f7029607)




![Screenshot 2023-08-03 101708](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/2c889da5-f69f-49e8-a14b-e73723d8870c)




* Are all of the rules in place? If not, then go back and make the necessary modifications before checking again.

Congratulations! You have successfully configured and deployed a fully comprehensive firewalld installation.


### Part 3: IDS, IPS, DiD and Firewalls

Now, you’ll work in another lab. Before you start, complete the following review questions.


#### IDS vs. IPS Systems



1. Name and define two ways an IDS connects to a network.

```
SPAN or Mirrored Port
A SPAN port is a function of an enterprise-level switch that allows you to mirror one or more physical switch ports to another port. A mirror image of all data will flow across both ports equally.
```



  


```
Network TAP
The most common type of TAP is an aggregated TAP, in which a cable connects the TAP monitor port with the NIC on the sensor. This specific placement allows traffic to be monitored between the router and switch.
```




2. Describe how an IPS connects to a network.

```
An IPS is usually connected Inline with the flow of data,between the firewall and the network switch.
```


3. What type of IDS compares patterns of traffic to predefined signatures and is unable to detect zero-day attacks?

```
Signature-based IDS compares patterns of traffic to predefined signatures. It is good for identifying well-known attacks and is vulnerable to attacks through packet manipulation. It is unable to detect zero-day attacks. 
```


4. What type of IDS is beneficial for detecting all suspicious traffic that deviates from the well-known baseline and is excellent at detecting when an attacker probes or sweeps a network?

```
Anomaly-based IDS compares patterns of traffic against a well-known baseline. It is good for detecting suspicious traffic that deviates from well-known baseline. It is excellent at detecting when attackers probe and sweep a network. Although, it is prone to false alerts.
```




#### Defense in Depth



1. For each of the following scenarios, provide the layer of defense in depth that applies:
   
    1. A criminal hacker tailgates an employee through an exterior door into a secured facility, explaining that they forgot their badge at home.

  ```
  Perimeter
  ```


    2. A zero-day goes undetected by antivirus software.

```
Application
```


    3. A criminal successfully gains access to HR’s database.

```
Data
```


    4. A criminal hacker exploits a vulnerability within an operating system.

```
Host
```


    5. A hacktivist organization successfully performs a DDoS attack, taking down a government website.

```
Network
```


    6. Data is classified at the wrong classification level.

```
Host
```


    7. A state-sponsored hacker group successfully firewalked an organization to produce a list of active services on an email server.

```
Network
```


2. Name one method of protecting data-at-rest from being readable on a hardSD drive.

```
Drive Encryption
```


3. Name one method of protecting data-in-transit.

```
Asymmetric Encryption and Hashing
```


4. What technology could provide law enforcement with the ability to track and recover a stolen laptop?

```
Police can get access to the laptop's identification information, where it's been logged into Wi-Fi networks, what phone modems it's been using and even its GPS tracking information.
```


5. How could you prevent an attacker from booting a stolen laptop using an external hard drive?

```
Find an option in your BIOS Setup to disable booting from an external hard drive and configure a BIOS Setup password.
```




#### Firewall Architectures and Methodologies



1. Which type of firewall verifies the three-way TCP handshake? TCP handshake checks are designed to ensure that session packets are from legitimate sources.

```
Circuit-Level Firewall
```


2. Which type of firewall considers the connection as a whole? Meaning, instead of considering only individual packets, these firewalls consider whole streams of packets at one time.

```
Stateful Packet Filtering Firewall
```


3. Which type of firewall intercepts all traffic prior to forwarding it to its final destination? In a sense, these firewalls act on behalf of the recipient by ensuring the traffic is safe prior to forwarding it.

```
Stateless Packet Filtering Firewall
```


4. Which type of firewall examines data within a packet as it progresses through a network interface by examining source and destination IP address, port number, and packet type—all without opening the packet to inspect its contents?

```
Application (Proxy) Firewall
```


5. Which type of firewall filters solely based on source and destination MAC address?

```
MAC Firewall
```




### Bonus Lab: “Green Eggs & SPAM”

In this activity, you will target spam, uncover its whereabouts, and attempt to discover the intent of the attacker.

 



* You will assume the role of a junior security administrator working for the Department of Technology for the State of California.

 



* As a junior administrator, your primary role is to perform the initial triage of alert data: the initial investigation and analysis followed by an escalation of high-priority alerts to senior incident handlers for further review.

 



* You will work as part of a Computer and Incident Response Team (CIRT), responsible for compiling **threat intelligence** as part of your incident report.


#### Threat Intelligence Card


```
Note: Log in to the Security Onion VM, and use the following indicator of attack to complete this portion of the assignment. 
```


Locate the indicator of attack in Sguil based off of the following:



* **Source IP/port**: `188.124.9.56:80`
* **Destination address/port**: `192.168.3.35:1035`
* **Event message**: `ET TROJAN JS/Nemucod.M.gen downloading EXE payload`

Answer the following questions:



1. What was the indicator of an attack? (_Hint: What do the details reveal?_)

```
Details indicate that the threat actor tried to download ET TROJAN JS, which downloads and runs other malicious files onto the system. 
```


2. What was the adversarial motivation (purpose of the attack)?

```
To get access to the system and steal private information.
```


3. Describe observations and indicators that may be related to the perpetrators of the intrusion. Categorize your insights according to the appropriate stage of the cyber kill chain, as structured in the following table:

<table>
  <tr>
   <td>
<strong>TTP</strong>
   </td>
   <td><strong>Example</strong>
   </td>
   <td><strong>Findings</strong>
   </td>
  </tr>
  <tr>
   <td><strong>Reconnaissance</strong>
   </td>
   <td>How did the attacker locate the victim?
   </td>
   <td>Hacker most likely did port scanning  of the target server to locate an open port. 
   </td>
  </tr>
  <tr>
   <td><strong>Weaponization</strong>
   </td>
   <td>What was downloaded?
   </td>
   <td>Downloaded malware called Trojan.
   </td>
  </tr>
  <tr>
   <td><strong>Delivery</strong>
   </td>
   <td>How was it downloaded?
   </td>
   <td>Once a hacker has accessed the terminal on the victim's machine, he/she would download the malware.
   </td>
  </tr>
  <tr>
   <td><strong>Exploitation</strong>
   </td>
   <td>What does the exploit do?
   </td>
   <td>Trojan typically downloads additional malware that would allow an attacker to take control of the system and steal private information.
   </td>
  </tr>
  <tr>
   <td><strong>Installation</strong>
   </td>
   <td>How is the exploit installed?
   </td>
   <td>The malware is installed in the background
   </td>
  </tr>
  <tr>
   <td><strong>Command & Control (C2)</strong>
   </td>
   <td>How does the attacker gain control of the remote machine?
   </td>
   <td>Through Privilege Escalation  and Lateral Movement.
   </td>
  </tr>
  <tr>
   <td><strong>Actions on Objectives</strong>
   </td>
   <td>What does the software that the attacker sent do to complete its tasks?
   </td>
   <td>This malware would deny user or organization access to files on their computer. By encrypting these files and demanding a ransom payment for the decryption key, the hacker places the organization in a position where paying the ransom is the easiest and cheapest way to regain access to their files. Some variants have added additional functionality – such as data theft – to provide furtincentive for ransomware victims to pay the ransom.
   </td>
  </tr>
</table>




4. What are your recommended mitigation strategies?

```
Some mitigation strategies

Identify Open Ports
Understand Port Usage
Know What Services Use Ports
Close the Riskiest Ports

To prevent Ransomware:

Robust Data Backup
Cyber Awareness Training
Strong, Secure User Authentication
Up-to-Date Patches
Anti-Ransomware Solutions

```


5. List your third-party references.

https://www.dnsstuff.com/ids-vs-ips
https://www.crowdstrike.com/cybersecurity-101/indicators-of-compromise/ioa-vs-ioc/
https://www.computer.org/publications/tech-news/trends/what-is-the-cyber-kill-chain-and-how-it-can-protect-against-attacks
https://www.checkpoint.com/cyber-hub/threat-prevention/ransomware/
https://securityscorecard.com/blog/how-can-you-secure-risky-open-ports
https://www.checkpoint.com/cyber-hub/threat-prevention/ransomware/how-to-prevent-ransomware/





© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
