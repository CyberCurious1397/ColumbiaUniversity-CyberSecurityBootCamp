# Project 1 Technical Brief

Make a copy of this document before you begin. Place your answers below each question. This completed document will be your deliverable for Project 1. Submit it through Canvas when you’re finished with the project at the end of the week.


## Your Web Application

Enter the URL for the web application that you created:




[mycybersecurityportfolio.com](https://www.mycybersecurityportfolio.com/)



Paste screenshots of your website created (Be sure to include your blog posts):


![Screenshot 2023-08-07 115439](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/d759986b-3faa-45e9-9797-ba2131ce15c1)



![Screenshot 2023-08-07 115546](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/20191bea-27e7-4572-a1e8-21d3c6835db6)



![Screenshot 2023-08-07 115656](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/3c81e8f1-d4e2-44bb-b9ae-8da10f5af842)



![Screenshot 2023-08-07 115825](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/ab549303-38a6-4831-9b62-4109ba647d18)



![Screenshot 2023-08-07 115947](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/2d5ce0fa-feb6-43c4-a7bc-44d403022ea3)



## Day 1 Questions


### General Questions



1. What option did you select for your domain (Azure free domain,  GoDaddy domain)?

```
Namecheap.com
```


2. What is your domain name?

```
mycybersecurityportfolio.com
```




### Networking Questions



1. What is the IP address of your webpage?

```
23.236.62.147
```


2. What is the location (city, state, country) of your IP address?

```
Council Bluffs, Iowa USA
```


3. Run a DNS lookup on your website. What does the NS record show?

```
Server: G3100.myfiosgateway.com
```




### Web Development Questions



1. When creating your web app, you selected a runtime stack.  What was it? Does it work on the front end or the back end? 

```
For my web app, I have selected PHP 7.4 runtime stack. PHP 7.4 is a server side (back end) programming language used to script websites that are dynamic and interactive.
```


2. Inside the `/var/www/html` directory, there was another directory called assets. Explain what was inside that directory.



![Screenshot 2023-08-07 120145](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/2f1fa3b6-da19-4f59-b8c6-f00e5429b25a)

![Screenshot 2023-08-07 120253](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/c4f0b886-ac4e-4941-812b-f258d97163bc)

```
Inside the assets directory, there are two other directories: CSS and Images.
Cascading Style Sheet(CSS) is used to set the style in web pages that contain HTML elements. It sets the background color, font-size, font-family, color, … etc property of elements on a web page. CSS saves a lot of work. It can control the layout of multiple web pages all at once. The other directory Images contains .jpg  .png files (pictures) for the web app.

```


3. Consider your response to the above question. Does this work with the front end or back end?

```
CSS and HTML are the Front End web languages.The programming languages used in the back end may include PHP, Java, Python, and Ruby.
```




## Day 2 Questions


### Cloud Questions



1. What is a cloud tenant?

```
A tenant is the most fundamental construct of a SaaS environment.. The customers that are signing up to use the provider's environment are represented as the tenants of its system. The software that is provided in this model is referred to as a multi-tenant SaaS system because each of the tenants of the service are consuming a single, shared system that supports the needs of these tenants through a unified experience. An update to the system, for example, would typically be applied to all tenants of that system.
(https://docs.aws.amazon.com/wellarchitected/latest/saas-lens/tenant.html)
```


2. Why would an access policy be important on a key vault?

```
A Key Vault access policy  is paramount on the key vault because it determines whether a given security "principal" can perform different operations on Key Vault secrets, keys, and certificates 
It should be tightly controlled on who has Contributor role access to key vaults to ensure that only authorized persons can access and manage your key vaults, keys, secrets, and certificates. 
(https://docs.microsoft.com/en-us/azure/key-vault/general/security-features)
```


3. Within the key vault, what are the differences between keys, secrets, and certificates?

```
 The Key Vault KEYS include two types of keys RSA key or EC key which are both asymmetric algorithms and enable the use of software-protected and HSM-protected keys..
The SECRETS provide secure storage of secrets, such as passwords and database connection strings. A secret is anything that's sensitive that's not an asymmetric key or a certificate, such as: an 256-bit AES symmetric key, a database connection string, a Kubernetes secret, an Application token. Finally, CERTIFICATES are X.509 v3 certificates and associated private keys. When a certificate is created, an addressable key and secret are also created with the same name. 
(https://michaelhowardsecure.blog/2021/04/29/the-relationship-between-keys-secrets-and-certificates-in-azure-key-vault/)
```




### Cryptography Questions



1. What are the advantages of a self-signed certificate?

```
Self-signed certificates are free. They are suitable for internal network websites and development/testing environments. 
```


2. What are the disadvantages of a self-signed certificate?

```
Browsers and Operating Systems do not trust self-signed certificates since a Publicly trusted CA does not sign them. Browsers would not show the green lock symbol or other visual indicators of trust.
Attackers can generate self-signed certificates, which can be used for man-in-the-middle (MITM) attacks, leaving users vulnerable to data theft and other forms of cyber-attacks.
(https://www.encryptionconsulting.com/education-center/self-signed-certificates/#:~:text=Advantages%3A,used%20by%20paid%20SSL%20certificates)
```


3. What is a wildcard certificate?

```
A wildcard certificate is a digital certificate that is applied to a domain and all its subdomains. Wildcard notation consists of an asterisk and a period before the domain name. Secure Sockets Layer (SSL) certificates often use wildcards to extend SSL encryption to subdomains. (https://www.techtarget.com/searchsecurity/definition/wildcard-certificate)
```


4. When binding a certificate to your website, Azure only provides TLS versions 1.0, 1.1, and 1.2.  Explain why SSL 3.0 isn’t provided.

```
SSL version 3.0 is no longer secure. In 2014, a team at Google discovered a serious vulnerability in SSL 3.0 that can be exploited to steal certain confidential information, such as cookies. This vulnerability, known as "POODLE", is similar to the BEAST attack. By exploiting this vulnerability, an attacker can gain access to things like passwords and cookies, enabling him to access a user's private account data on a website.
(https://blog.mozilla.org/security/2014/10/14/the-poodle-attack-and-the-end-of-ssl-3-0/)
```


5. After completing the Day 2 activities, view your SSL certificate and answer the following questions:
   
    a. Is your browser returning an error for your SSL certificate? Why or why not?

```
The browser does not return an error for the SSL certificate. Certificate for my website was issued by R3. R3 (Let's Encrypt) is a free SSL Certificate provider, issuing certificates automatically but only for 3 months.
```

![Screenshot 2023-08-07 120445](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/ce50705b-1904-4096-84f4-206cb4b160d1)

    b. What is the validity of your certificate (date range)?

```
8/31/2022 to 11/29/2022
```


    c. Do you have an intermediate certificate? If so, what is it?

```
Yes.  R3 (Let's Encrypt) is intermediate certificate authority
```


    d. Do you have a root certificate? If so, what is it?


```
Yes, I do. It is ISRG Root X1
```

![Screenshot 2023-08-07 120834](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/f5191bd1-8851-46ab-bb2b-f78b5b93554c)


    e. Does your browser have the root certificate in its root store?

```
Yes, it does. I am using Chrome browser and it uses Windows certificate store.
```


    f. List one other root CA in your browser’s root store.

```
AAA Certificate Services
```

![Screenshot 2023-08-07 121314](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/ebc82223-3971-49af-9d8d-057f58d0109f)




## Day 3 Questions


### Cloud Security Questions 



1. What are the similarities and differences between Azure Web Application Gateway and Azure Front Door?

```
Some of the similarities are: it both reside in front of the web application in order to protect it, they work on the Application Layer 7 of the OSI model, their primary solution is load balancer, they can incorporate a web application firewall(WAF) to protect against web vulnerability attacks and they have additional features such as URL path-based routing and SSL/TLS termination. Some of the differences are: The Web Application Gateway is more regional, to protect a web application in a single region in my cloud. The Azure Front Door is more global and is better suited when there are variety of regions in a cloud environment.
```


2. A feature of the Web Application Gateway and Front Door is “SSL Offloading.” What is SSL offloading? What are its benefits?

```
SSL Offloading is the process when SSL encryption is removed from incoming traffic to free up a web server from the work of decrypting or encrypting traffic sent via SSL and offloaded to a separate device designed specifically for SSL acceleration or SSL termination.
The benefits of SSL Offloading are:
It increases internet load speed time.
Improves web server performance
Increases website stability.
Assists in auto scaling the web servers during the peak hours of traffic.
Provides greater security to ward off malicious attacks.
```


3. What OSI layer does a WAF work on?

```
Web Application Firewall (WAF) is a part of layer 7 defense. It is designed to examine all HTTP or HTTPs traffic between external users and web applications. It detects and prevents malicious sources from gaining access to users or web applications.
bnm
(https://www.l7defense.com/solutions/web-application-firewall/)
```


4. Select one of the WAF managed rules (e.g., directory traversal, SQL injection, etc.), and define it.

```
Application Gateway Web Application Firewall (WAF) protects web applications from common vulnerabilities and exploits. This is done through rules that are defined based on the OWASP core rule sets.I have selected SQL injection to define below.
SQL Injection Attack  happens when a threat actor inserts or injects SQL query in input data from client to the application in order to exploit sensitive data from the database, modify database data, execute administration  operations on the database, and issue commands to the operating system. SQL Injection Attacks allow threat actors to spoof identity, tamper with existing data, void transactions or change balances, etc. 
SQL Injection  is very common with PHP and ASP applications. WAF detects and blocks malicious SQL code in web requests.
```


5. Consider the rule that you selected. Could your website (as it is currently designed) be impacted by this vulnerability if Front Door wasn’t enabled? Why or why not?

```
Mywebsite mycybersecurityportfolio.com could be impacted by SQL Injection Attack if Front Door wasn't enabled, because my website uses PHP backend language, it is susceptible to SQL Injection. There are different places on my website where visitors could input or insert information, therefore it is vulnerable.
```


6. Hypothetically, say that you create a custom WAF rule to block all traffic from Canada. Does that mean that anyone who resides in Canada would not be able to access your website? Why or why not? 

```
If a WAF rule would be created blocking all traffic from Canada, it does not mean that everyone who resides in Canada would not be able to access my website, because Geo-filtering works based on mapping each request's IP address to a country or region. There might be some IP addresses in the data set that are not yet mapped to a country or region. To avoid accidentally blocking legitimate users, Application Gateway's WAF allows requests from unknown IP addresses. Therefore, devices with unknown IP located in Canada can still access it. Also, devices connected through VPN can access my website as well.
```


7. Include screenshots below to demonstrate that your web app has the following:
    1. Azure Front Door enabled

![Screenshot 2023-08-07 121530](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/85511912-c984-420e-bea9-82d6f1677e76)


    2. A WAF custom rule

![Screenshot 2023-08-07 121629](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/b9d61aea-651d-42f3-8935-ac94d50f5090)





## Disclaimer on Future Charges 

Please type “**YES**” after one of the following options:



* **_Maintaining website after project conclusion: I am aware that I am responsible for any charges that I incur by maintaining my website. I have reviewed the [guidance](https://docs.google.com/document/d/1ZzC4oTJFdlkkeWuzuJAyVSqtDFbuAWilmwXg8PZgzMs/edit) for minimizing costs and monitoring Azure charges. —   _YES**
* **_Disabling website after project conclusion: I am aware that I am responsible for deleting all of my project resources as soon as I have gathered all of my web application screen shots and completed this document._**

© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
