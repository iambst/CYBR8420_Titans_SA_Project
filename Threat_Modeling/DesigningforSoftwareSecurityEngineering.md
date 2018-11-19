
## Threat Model Diagram
### Threat Model Level-0
Web Browser makes HTTPS request to Nextcloud logic API for customer data. Nextcloud logic API verifies input and retrieves data from Nextcloud database. Required data is then sent to the web browser as HTTPS response. 

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Threat_Modeling/Level-0.JPG "Level -0")

### Threat Model Level-1
The following Level-1 diagram expands the Level-0 diagram further by including details of major processes, related databases and dataflow interactions between them.

[Threat Model Report Level - 1](http://htmlpreview.github.com/?https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Threat_Modeling/Threat_Report_R3.htm)

## Summary of Observations

### Spoofing

Nextcloud has built-in two-factor authentication. It also has mechanisms like Time-based One-Time Password and Universal 2nd Factor which require password confirmation when changing their settings to ensure a malicious attacker cannot simply disable them. Universal 2nd Factor can have multiple tokens and there is also is support for near field communication (NFC) tokens. Two-factor authentication actions also show up in the Activities. This lets user keep an eye on when and where logins take place. Additionally, credentials when transferred are also encrypted. 

### Tampering

* Nextcloud uses Content-Security-Policy to prevent the execution of inline JavaScript code. This mitigates cross site scripting. Additionally, Nextcloud suggests developers of Nextcloud Server related apps that the user has to sanitize the templates and all JavaScripts which performs a DOM manipulation.

* Nextcloud also uses prepared queries. If App framework is used, it mentions the user to use the syntax to extend mapper class.

### Repudiation

Nextcloud provides a wide range of logging levels from DEBUG, which logs all activity, to FATAL, which logs only fatal errors. Logging level parameters are set in the config/config.php file, or on the Admin page of Nextcloud Web GUI. By default, a log file named nextcloud.log will be created in the directory which has been configured by the datadirectory parameter in config.php. All log information will be sent to default syslog daemon. 

This audit logs include user session information, file handling, user management, sharing and other actions. 

However, at the moment Nextcloud doesnot provide logs for non-critical activities like "Accessing previews of files". It is mentioned that this logs will be added in future releases.

### Information Disclosure

Nextcloud offers multiple layers of encryption for the data. 

First, data is protected when being transferred between clients and servers as well as between servers.  Nextcloud uses standard TLS, a secure communication protocol used by HTTPS. It also warns system administrators strongly if it is not turned on.

Second, data can be encrypted on storage. The Nextcloud Server Side Encryption feature provides secure storage of data by encrypting each file with a unique file key before it is stored. File keys are encrypted, in turn, either by a server wide key  or a per-user key. Server Side Encryption provides protection for data on external storage as the files are encrypted before they are sent to storage. 

Thirdly, Nextcloud offers end-to-end encryption on the client side. The Nextcloud End to End encryption feature is designed such that the server never has access to unencrypted files or keys, nor does server-provided code ever handle unencrypted data which could provide avenues for compromise. Cryptographic Identity Protection in the form of server signed certificates and a Trust On First Use (TOFU) model protects against attackers trying to impersonate other users. 


### Denial of Service

Nextcloud uses the bcrypt algorithm to prevent Denial of Service, as CPU demand increases exponentially, it only verifies the first 72 characters of passwords. This applies to all passwords that are used in Nextcloud including user passwords, passwords on link shares, and passwords on external shares.

However, Nextcloud uses PHP scripting language. In 2011 the Chaos Computer Club revealed a major complexity attack vulnerability that works across all major languages including PHP. PHP addressed the vulnerability for forms but never really fixed it. 

For this reason while Nextcloud do fix and acknowledge specific Denial of Service attacks they generally do not consider DoS a high-risk vulnerability.

### Elevation of Privilege

Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.

* OCP\JSON::checkLoggedIn() -  Checks if the logged in user is logged in
* OCP\JSON::checkAdminUser()-  Checks if the logged in user has admin privileges
* OCP\JSON::checkSubAdminUser()- Checks if the logged in user has group admin privileges

These checks are automatically performed for each request and have to be explicitly turned off by using annotations if necessary. 


## Nextcloud accepted risks:

### Administrator privileges
Nextcloud administrators are ultimately trusted. It is for example expected behavior that a Nextcloud administrator can execute arbitrary code.
### Denial of Service
Due to the usage of the PHP scripting language we do consider Denial of Service not something that can at the moment be completely prevented in Nextcloud. For this reason nextcloud fixes and acknowledges specific Denial of Service attacks.
### Local external storage systems are considered trusted
Next cloud considers local mounted storage systems as trusted, so if a symlink or something else is configured on the external storage the Nextcloud server will follow it with the web server privileges.For this reason administrators are recommended to only use the external storage mount for ultimately trusted content.
### Server-side encryption
Nextcloud can be configured to encrypt data at rest. This has two options: server-wide key (default since Nextcloud 13) or per-user key. With the former, the keys are on the server and thus the only protection offered is against external storage. With per-user keys, the keys are encrypted by the user password and handled as securely as possible, thus securing data when the user is not logged in.  Nextcloud administrator could still intercept the user password to manually decrypt the encryption key. So nextcloud only considers attack scenarios bounty-worthy if they include an external storage vector or, with per-user-keys, data-at-rest.
### Client-side encryption
Nextcloud client-side (or end-to-end) encryption is designed to protect user data from the server in nearly all scenario's. Any way to circumvent the protection as covered by the security properties would be treated by us as a security issue. 
### Features intentionally marked as insecure
Some features in Nextcloud are intentionally marked as insecure and disabled by default (plus have a big warning above them). One example includes the preview providers such as the LibreOffice preview provider.
### Audit logging
The audit logging feature in Nextcloud is at the moment missing some logs for things like "Accessing previews of files", these will be added in a future release and known issues are tracked in issue tracker. 
### Version disclosure
Next cloud considers version disclosure an accepted risk as an attacker can enumerate service versions using other means as well. (e.g. comparing behaviour)
### Attacks involving other Android apps on the device
Nextcloud considers attacks involving other Android apps on the device as low or medium risk. Stored files can be hidden from other apps if appropriate storage option is selected inside the app. This should be secure, however, if the phone is compromised Nextcloud doesnot guarantee data safety.
### Content spoofing
Next cloud does not consider content spoofing as a bounty-worthy vulnerability.
### User enumeration
Nextcloud considers user enumeration a security risk as for convenience and for features such as Server-to-Server sharing it is considered as an expected behaviour.
### Brute force of credentials
Nextcloud 12 introduced brute force protection. If user finds a way in which it is broken, it could qualify as a security issue. Nextcloud states that using TOR or similar solutions can be used to circumvent IP address based brute force protection. It is also not implemented in all endpoints, but should not allow guessing passwords at great speed from a single IP address.
### Server-side request forgery
Nextcloud ships with multiple features that perform sending requests to other hosts, Nextcloud considers this accepted behaviour and advocates people to deploy Nextcloud into its own seggregated network segment.





[Trello Project Board](https://trello.com/b/PG39aw1z/sa-project-task-4-threat-modeling)
