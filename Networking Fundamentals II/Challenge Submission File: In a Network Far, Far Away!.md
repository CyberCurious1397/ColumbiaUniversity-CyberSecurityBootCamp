## **In a Network Far, Far Away!**

Make a copy of this document to work in, and then for each mission, add the solution below the prompt. Save and submit this completed file as your Challenge deliverable.


### **Mission 1**



1. Mail servers for starwars.com:


![Screenshot 2023-08-03 092123](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/bd020931-9248-483d-a688-6dcd2296047f)



```
starwars.com    mail exchanger = 1 aspmx.l.google.com.
starwars.com    mail exchanger = 5 alt1.aspx.l.google.com.
starwars.com    mail exchanger = 5 alt2.aspmx.l.google.com.
starwars.com    mail exchanger = 10 aspmx2.googlemail.com.
starwars.com    mail exchanger = 10 aspmx3.googlemail.com.
```




2. Explain why the Resistance isn’t receiving any emails:

```
It looks like The Resistance isn't able to receive any emails because, as indicated in their MX records, the correct primary and secondary mail servers are not listed. It should have listed asltx.l.google.com and asltx.2.google.com as their corresponding mail servers.

```


3. Suggested DNS corrections:

```
DNS records have to be corrected to indicate the following:
starwars.com     mail exchanger = 1 asltx.l.google.com.
starwars.com     mail exchanger = 5 asltx.2.google.com.
```




### **Mission 2**



1. Sender Policy Framework (SPF) of `theforce.net`:


![Screenshot 2023-08-03 092310](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/9432bb2b-923a-409d-8342-b537e9cec487)



```
theforce.net	text = "v=spf1 a mx mx:smtp.secureserver.net include:aspmx.googlemail.com ip4:104.156.250.80 ip4:45.63.15.159 ip4:45.63.4.215"
```




2. Explain why the Force’s emails are going to spam:

```
The Force's emails are going to the spam folder beacuse they didnt update their DNS text record to list all the servers and IP addresses authorized to send emails.The record should have included IP address "45.23.176.21" for new mail server.
```


3. Suggested DNS corrections:



![Screenshot 2023-08-03 092359](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/1fa59427-5159-4204-9948-d0c2eaff9a26)



```
Suggested DNS corrections are:
theforce.net text = "v=spf1 a mx mx:smtp.secureserver.net include:aspmx.googlemail.com include:45-23-176-21.lightspeed.rcsntx.sbcglobal.net 
ip4:104.156.250.80 ip4:45.63.15.159 ip4:45.63.4.215 ip4:45.23.176.21"
```



### **Mission 3**



1. Document the CNAME records:



![Screenshot 2023-08-03 092431](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/49211424-3f83-4da2-a6f7-918b91fe8183)


```
www.theforce.net        canonical name = theforce.net.
```




2. Explain why the subpage `resistance.theforce.net` isn’t redirecting to `theforce.net`:

```
Their DNS record is missing a reference of resistance.theforce.net to theforce.net
```


3. Suggested DNS corrections:

```
Would need to add reference as follows:
www.theforce.net         canonical name = theforce.net. resistance.theforce.net  canonical name = www.theforce.net.
```




### **Mission 4**



1. Confirm the DNS records for `princessleia.site`:



![Screenshot 2023-08-03 092514](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/ca7ca77b-7bb6-44f1-848c-d205241ba595)



```
princessleia.site	    nameserver = ns25.domaincontrol.com.
princessleia.site	    nameserver = ns26.domaincontrol.com.
```




2. Suggested DNS record corrections to prevent the issue from occurring again:

```
They would need to add the reference to the backup DNS server as follows:
princessleia.site       nameserver = ns26.domaincontrol.com. princessleia.site       nameserver = ns2.galaxybackup.com.  
```




### **Mission 5**



1. Document the shortest `OSPF` path from Batuu to Jedha:


![Screenshot 2023-08-03 092557](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/08e0c3ef-e793-4f50-8b99-2002e3b9680c)




    1. `OSPF` path:

```
The shortest path is as follows:
Batuu > D > C > E > F > J > I > L > Q > T > V > Jedha
      1   2   1   1   1   1   6   4   2   2   2  = 23 hops
```


    2. `OSPF` path cost:

```
1   2   1   1   1   1   6   4   2   2   2  = 23 
```




### **Mission 6**



1. Wireless key:


![Screenshot 2023-08-03 092647](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/d48b5ba5-83fb-4112-b276-b430e7105970)


```
dictionary:linksys
```




2. Host IP addresses and MAC addresses: 
    1. Sender MAC address:

```
00:0f:66:e3:e4:01
```


    2. Sender IP address:

```
172.16.0.1
```


    3. Target MAC address:

```
00:13:ce:55:98:ef
```


    4. Target IP address:

```
172.16.0.101 
```




### **Mission 7**



1. Screenshot of results:



![Screenshot 2023-08-03 092747](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/4226823d-f643-442f-913a-7cfda7afe844)




![Screenshot 2023-08-03 092823](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/0f444476-af29-4f46-970a-c948f141e577)


© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
