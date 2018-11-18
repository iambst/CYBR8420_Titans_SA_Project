
## Threat Model Diagram
[Threat Model Report](http://htmlpreview.github.com/?https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Threat_Modeling/Threat_Report_R1.htm)

## Threat Model Analysis
### Threat: Elevation Using Impersonation
### Mitigation:
Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.
*	OCP\JSON::checkLoggedIn(): Checks if the logged in user is logged in
*	OCP\JSON::checkAdminUser(): Checks if the logged in user has admin privileges
*	OCP\JSON::checkSubAdminUser(): Checks if the logged in user has group admin privileges.
Using the App Framework, these checks are already automatically performed for each request and have to be explicitly turned off by using annotations.

### Threat:Spoofing of the Third-Party WebServer External Destination Entity
### Mitigation:
Nextcloud can be run through a reverse proxy, which can cache static assets such as images, CSS or JS files, move the load of handling HTTPS to a different server or load balance between multiple servers.Next cloud emphasizes to define the trusted proxies parameter  as an array of IP address to define the servers Nextcloud should trust as proxies. Nextcloud uses the de-facto standard header ‘X-Forwarded-For’ by default, but this can be configured with the forwarded_for_headers parameter. This parameter is an array of PHP lookup strings, for example ‘X-Forwarded-For’ becomes ‘HTTP_X_FORWARDED_FOR’. If the parameter is set incorrectly there is a chance for clients to spoof their IP address as visible to Nextcloud, even when going through the trusted proxy.

### Threat:External Entity Third-Party WebServer Potentially Denies Receiving Data
### Mitigation:
In Nextcloud server data storage can be encrypted using a default military grade AES-256 encryption with server-based or custom key management which prevents external entity writing data.

### Threat:Data Flow Checks User Access Rights Is Potentially Interrupted
### Mitigation:
Data Transfer from Nextcloud employs industry-standard TLS to encrypt data in transfer. This prevents interruption of data flow across a trust boundary in either direction.

### Threat:Spoofing of Destination Data Store NextCloud Database
### Mitigation:
In Nextcloud server data storage can be encrypted using a default military grade AES-256 encryption with server-based or custom key management which prevents external entity write data.

### Threat:Potential SQL Injection Vulnerability for NextCloud Database
### Mitigation:
Next cloud emphasises to use prepared queries.If App framework is used it mentions the user to use the syntax to extend mapper class But it doesnot provide any mechanism to stop SQL injection.

### Threat:Potential Excessive Resource Consumption for NextCloud Storage API or NextCloud Database
### Mitigation:
There is no proper mitigation against Denial of Service attacks. Due to the usage of the PHP scripting language Next cloud considers Denial of Service not something that can at the moment be completely prevented. 

### Threat:Spoofing the NextCloud Storage API Process
### Mitigation:
In Nextcloud server data storage can be encrypted using a default military grade AES-256 encryption with server-based or custom key management which prevents external entity write data.

### Threat:The NextCloud Database Data Store Could Be Corrupted
### Mitigation:
Data flow to the datastore in Nextcloud is secured. Data Transfer from Nextcloud employs industry-standard TLS to encrypt data in transfer. This prevents interruption of data flow to the data store.

### Threat:Data Store Denies NextCloud Database Potentially Writing Data
### Mitigation:
In Nextcloud server data storage can be encrypted using a default military grade AES-256 encryption with server-based or custom key management which prevents external entity writing data.

### Threat:Data Flow Sniffing
### Mitigation:
Sniffing of data Data flowing across Customer Data Request is mitigated in Nextcloud server by provides encryption during data transfer. This is done by employing industry-standard TLS to encrypt data in transfer in Nextcloud.

### Threat:Weak Credential Transit
### Mitigation:
Nextcloud has built-in two-factor authentication. It also has mechanisms like TOTP and U2F which  require password confirmation when changing their settings to ensure a malicious attacker cannot simply disable them. Second, U2F can have multiple tokens; and there is also is support for NFC tokens. 2FA actions also show up in the Activities app so you can keep an eye on when and where logins take place. Moreover credentials when transferred are also encrypted. The links shared are password protected.

### Threat:Data Flow Customer Data Request Is Potentially Interrupted
### Mitigation:
Data Transfer from Nextcloud employs industry-standard TLS to encrypt data in transfer. This prevents interruption of data flow across a trust boundary in either direction.

### Threat:Data Store Inaccessible
### Mitigation:
In Nextcloud server data storage can be encrypted using a default military grade AES-256 encryption with server-based or custom key management which prevents external entity to access data store on the other side of the trust boundary.

### Threat:Elevation Using Impersonation
### Mitigation:
Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.OCP\JSON::checkLoggedIn(): Checks if the logged in user is logged in,OCP\JSON::checkAdminUser(): Checks if the logged in user has admin privileges,OCP\JSON::checkSubAdminUser(): Checks if the logged in user has group admin privileges.Using the App Framework, these checks are already automatically performed for each request and have to be explicitly turned off by using annotations.

### Threat:Cross Site Scripting
### Mitigation:
 Cross site scripting happens when user input is passed directly to templates. A potential attacker might be able to inject HTML/JavaScript into the page to steal the users session, log keyboard entries, even perform DDOS attacks on other websites or other malicious actions. Despite the fact that Nextcloud uses Content-Security-Policy to prevent the execution of inline JavaScript code developers are still required to prevent XSS. CSP is just another layer of defense that is not implemented in all web browsers. To prevent XSS in next cloud app	 user has to sanitize the templates and all JavaScripts which performs a DOM manipulation. If not there is a chance of Cross site Scripting.

### Threat:Spoofing the Web Browser External Entity
### Mitigation:
Nextcloud provides Two-factor authentication (2FA) It is a way to protect your Nextcloud account against unauthorized access. It works by requiring two different ‘proofs’ of your identity. For example, something you know (like a password) and something you have like a physical key. Typically, the first factor is a password like you already have and the second can be a text message you receive or a code you generate on your phone or another device (something you have). Nextcloud supports a variety of 2nd factors and more can be added.

### Threat:Potential Data Repudiation by NextCloud Logic API
### Mitigation:
In next cloud server 2FA actions also show up in the Activities app so you can keep an eye on when and where logins take place. The user gets notifications on phone and desktop when a user on another cloud server shares files. This kind of prevents External Entity from denying the data being received. But the audit logging feature in Nextcloud is at the moment missing some logs for things like "Accessing previews of files".

### Threat:Potential Process Crash or Stop for NextCloud Logic API
### Mitigation:
Due to usage of PHP scripting language there is potential chance for Denial of Service attacks.Though next cloud deals with a few denial service attacks it doesnot prevent all of them and there were numerous points where the was running slowly and crashed.

### Threat:Data Flow HTTPS Request Is Potentially Interrupted
### Mitigation:
Data Transfer from Nextcloud employs industry-standard TLS to encrypt data in transfer. This prevents interruption of data flow across a trust boundary in either direction.

### Threat:NextCloud Logic API May be Subject to Elevation of Privilege Using Remote Code Execution
### Mitigation:
Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.OCP\JSON::checkLoggedIn(): Checks if the logged in user is logged in,OCP\JSON::checkAdminUser(): Checks if the logged in user has admin privileges,OCP\JSON::checkSubAdminUser(): Checks if the logged in user has group admin privileges.Using the App Framework, these checks are already automatically performed for each request and have to be explicitly turned off by using annotations.

### Threat:Elevation by Changing the Execution Flow in NextCloud Logic API
### Mitigation:
Nextcloud offers three simple checks to prevent additional privileges by attacker or Auth bypass.OCP\JSON::checkLoggedIn(): Checks if the logged in user is logged in,OCP\JSON::checkAdminUser(): Checks if the logged in user has admin privileges,OCP\JSON::checkSubAdminUser(): Checks if the logged in user has group admin privileges.Using the App Framework, these checks are already automatically performed for each request and have to be explicitly turned off by using annotations.

### Threat:Cross Site Request Forgery
### Mitigation:
To prevent CSRF in an app, Nextcloud emphasizes to be sure to call the following method at the top of all user files:
* OCP\JSON::callCheck();
If user uses the App Framework, every controller method is automatically checked for CSRF unless you explicitly exclude it by setting the @NoCSRFRequired annotation before the controller method. 

### Threat:Spoofing of the Web Browser External Destination Entity
### Mitigation:
Nextcloud provides Two-factor authentication (2FA). It is a way to protect your Nextcloud account against unauthorized access. It works by requiring two different ‘proofs’ of your identity. For example, something you know (like a password) and something you have like a physical key. Typically, the first factor is a password like you already have and the second can be a text message you receive or a code you generate on your phone or another device (something you have). Nextcloud supports a variety of 2nd factors and more can be added.

### Threat:External Entity Web Browser Potentially Denies Receiving Data
### Mitigation:
In next cloud server 2FA actions also show up in the Activities app so you can keep an eye on when and where logins take place. The user gets notifications on phone and desktop when a user on another cloud server shares files. This kind of prevents External Entity from denying the data being received. But the audit logging feature in Nextcloud is at the moment missing some logs for things like "Accessing previews of files".

## Summary and observations of Threats
Of all the threats Identified, we found threats majorly categorized into five main categories:
* Spoofing
* Denial of Service.
* Repudiation.
* Tampering.
* Elevation of Privilege.
* Information Disclosure.
We identifies the following threats as high priority:
### Threat:Spoofing of the Third-Party WebServer External Destination Entity
### Mitigation:
### Threat:Data Flow Checks User Access Rights Is Potentially Interrupted
### Mitigation:
### Threat:Spoofing of Destination Data Store NextCloud Database
### Mitigation:
### Threat:Cross Site Request Forgery
### Mitigation:
### Threat:Potential Excessive Resource Consumption for NextCloud Storage API or NextCloud Database
### Mitigation:
### Threat:Data Flow Sniffing
### Mitigation:
### Threat:Cross Site Scripting
### Mitigation:
### Threat:Weak Access Control for a Resource
### Mitigation:
Next cloud accepts certain risks and the analysis is present below for the accepted risks.
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
