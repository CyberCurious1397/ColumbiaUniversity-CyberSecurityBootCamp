## Testing Web Applications for Vulnerabilities

Make a copy of this document to work in, and then respond to each question below the prompt. Save and submit this completed file as your Challenge deliverable.


### Web Application 1: _Your Wish is My Command Injection_

Provide a screenshot confirming that you successfully completed this exploit:



![Screenshot 2023-08-08 105950](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/bd20cbaa-d487-448c-9f09-f49baf868c0f)




![Screenshot 2023-08-08 110003](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/cd072c4a-d52a-4bad-a124-3b96119ae4ec)



![Screenshot 2023-08-08 110020](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/fa30d96c-4b01-4e22-9d53-660f6da67850)


/etc/hosts


![Screenshot 2023-08-08 110048](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/09e5bce1-e457-48cd-b5f0-7e56f005c07c)
![Screenshot 2023-08-08 110102](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/5d491cbf-e194-4e38-b8f0-249e9f8ac1af)

Write two or three sentences outlining mitigation strategies for this vulnerability: 


```
Mitigation for directory traversal attack:
Limit the user input when calling for files from the web application
There should be input validation set up using a whitelist approach.
Web servers should run under a special service user account that only has access to that web folder.
```



### Web Application 2: _A Brute Force to Be Reckoned With_

Provide a screenshot confirming that you successfully completed this exploit:


```
Following was intercepted by Burp Suite under the proxy tab.
```



![Screenshot 2023-08-08 114627](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/6f442e9b-7ef9-4a91-9ddf-44b02904944d)


I have forwarded the above info to Burp Intruder, where I was able to load usernames and passwords given and start the attack using Cluster Bomb under Intruder Burp Suite. It was able to successfully log in with tonystark username and I am Iron Man password.



![Screenshot 2023-08-08 114643](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/d7f46580-dfa1-47ff-b8ff-f8050e3f9323)
![Screenshot 2023-08-08 114659](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/cd978214-01a3-4f9c-bd23-ce1a9535d342)


Write two or three sentences outlining mitigation strategies for this vulnerability: 


```
The ways to prevent or mitigate Brute Force Attacks:
Use Strong Passwords. 
Limit Login Attempts. 
Monitor IP addresses. 
Use Two-Factor Authentication (2FA).
Use CAPTCHAs.
Use Unique Login URLs. 
Disable Root SSH Logins.
Use Web Application Firewalls (WAFs)

Cited Information
(https://www.itsasap.com/blog/how-to-prevent-brute-force-attacks)

```



### Web Application 3: _Where's the BeEF?_

Provide a screenshot confirming that you successfully completed this exploit:

1.Step >>> Set up BeEF



![Screenshot 2023-08-08 114900](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/69a526f1-8b0d-4de1-93f4-dce791364c74)


2. Step >>>> Opened hooked website



![Screenshot 2023-08-08 114918](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/da9aafdf-f779-4f2a-a630-7b49ae057db4)


3. Step >>>> Check the details in BeEF. Performed Google Phishing exploit on the hooked website. Obtained username and password.


![Screenshot 2023-08-08 114936](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/98ec9d79-5aaa-43fc-aaf3-39a5153d0170)
![Screenshot 2023-08-08 114954](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/0ca606ef-24fb-42a8-ac75-f733482ef48b)


 4. Step >>> Hooking Replicants web application. Inserting payload in the message section by increasing text size in the dev tools of the page.



![Screenshot 2023-08-08 115012](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/fc2ecf00-2131-4d60-96a3-d7d312d4c3f9)


5. Step >>>> Performing BeEF exploits on the hooked website.

Social Engineering > Pretty Theft

The Fake Facebook Login pop-up section came up and asked user for username and password.

![Screenshot 2023-08-08 120409](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/3db28be4-774f-4035-836e-2343ec46c13d)

![Screenshot 2023-08-08 115332](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/0ada1a7a-0dc4-4d1d-bf88-3af893a95e55)


Social Engineering > Fake Notification Bar

Notification to install the plugin came up. 



![Screenshot 2023-08-08 115355](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/997ea6b0-c6b9-4e04-85b5-5c0290098715)



![Screenshot 2023-08-08 115757](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/427eab29-a83d-435a-b923-04024aec4725)



Host > Get Geolocation (Third Party)



![Screenshot 2023-08-08 115824](https://github.com/CyberCuriosity8586/ColumbiaUniversity-CyberSecurityBootCamp/assets/105434347/07a842ff-3208-4f57-8189-e65cdabe097a)





Write two or three sentences outlining mitigation strategies for this vulnerability: 


```
Things to do to prevent this vulnerability:

Need to keep a healthy Content-Security-Policy, where the browser would refuse to load the external beef hook.
Create strict front-end and back-end input validations.
Perform constant social engineering cyber defense training.
Keep constant password hygiene  
```


© 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
