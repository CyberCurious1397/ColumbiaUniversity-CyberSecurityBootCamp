## **Networking Fundamentals: Rocking your Network**

Make a copy of this document to work in, and then for each phase, add the solution below the prompt. Save and submit this completed file as your Challenge deliverable.


### Phase** 1: “I’d like to Teach the World to <code>ping</code>”</em></strong>

1. Command(s) used to run `fping` against the IP ranges:
   
  * `fping -g 15.199.95.91/28`
  * `fping -g 15.199.94.91/28`
  * `fping -g 11.199.158.91/28`
  * `fping -g 167.172.144.11/32`
  * `fping -g 11.199.141.91/28`



2. Summarize the results of the `fping` command(s):


![Screenshot 2023-08-02 160425](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/6acd251c-6b00-41d0-906a-4008a4b82a49)


```
Almost all IP addresses were unreachable except 3 listed below.
```


3. List of IPs responding to echo requests:

```
IP addresses 192.0.2.2 192.0.2.4 161.35.96.20 are alive and respond to ping.

```


4. Explain which OSI layer(s) your findings involve:

```
My findings involve the 3rd Network Layer of OSI model.

```


5. Mitigation recommendations (if needed):

```
Further investigation is required. It is recommended to restrict allowing ICMP echo requests against those IP addresses.
```




### Phase** 2: _“Some SYN for Nothin`”_**



1. Which ports are open on the RockStar Corp server?

![Screenshot 2023-08-02 160713](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/91260cc5-3a84-494d-8388-62b8db79b98c)

```
Port 22  SSH is open
```


2. Which OSI layer do SYN scans run on?
   
    1. OSI Layer:

```
Transport - Layer 4

```


    2. Explain how you determined which layer:

```
At this Transport layer number 4, the transmission data and the destination ports are added to the TCP header and different handshakes are starting to happen. Because we did SYN scans on the IPs to see which ports are accepting the signal, this information gives us the hint that this is going on the transport layer of the OSI model.

```


3. Mitigation suggestions (if needed):

```
To mitigate the threat of having an open port, I would suggest closing that port if it is not actively needed or restrict port access to specific source IP addresses.

```




### Phase** 3: _“I Feel a DNS Change Comin’ On”_**



1. Summarize your findings about why access to rollingstone.com is not working as expected from the RockStar Corp Hollywood office:

```
After initiating ssh session through port 22 
<sudo ssh jimi@161.35.96.20> with password: hendrix, I was able to check the /etc/hosts file for the IP address of rollingstone.com. It appears that the IP address for rollingstone.com has been modified to 98.137.246.8. It is a threat since etc/hosts was modified by someone.

```

![Screenshot 2023-08-02 160921](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/a65a94d8-09cf-4490-a1d7-2693cf288fef)



2. Command used to query Domain Name System records:

```
Nslookup 98.137.246.8

```


3. Domain name findings:


![Screenshot 2023-08-02 161045](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/6ad48388-5ef0-49cb-8fbf-6b6003bf05ce)


```
name=unknown.yahoo.com

```




4. Explain what OSI layer DNS runs on:

```
DNS runs on the Application Layer #7 in OSI model, because it is essentially an application that invokes to help out HTTP application.
```


5. Mitigation suggestions (if needed):

```
I would suggest to disable port 22 in sshd_config file.
```




### Phase 4: “ShARP Dressed Man”



1. Name of file containing packets:


![Screenshot 2023-08-02 161202](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/5a6e4dcd-32f0-4f76-8831-a65336a21a66)



```
packetcaptureinfo.txt

```


2. ARP findings identifying the hacker’s MAC address:


![Screenshot 2023-08-02 161257](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/205dce15-190d-473e-af59-0aa6493fb75e)



```
00:0c:29:1d:b3:b1

```




3. HTTP findings, including the message from the hacker:



![Screenshot 2023-08-02 161405](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/c491f1a9-51b1-455f-bf84-ccde688dff56)


```
Hacker sent an email above.

```




4. Explain the OSI layers for HTTP and ARP.

    1. Layer used for HTTP:

```
Layer 7 - Application: Hacker sent an email with his intentions.
```


    2. Layer used for ARP:

```
Layer 2 - Data Link: ARP Protocol was used to transfer network traffic within the local network.
```


5. Mitigation suggestions (if needed):

```
I would suggest creating a static ARP entry.
```



© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
