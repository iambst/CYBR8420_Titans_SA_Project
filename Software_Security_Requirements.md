# Requirements for Software Security Engineering

## Backstory

Nextcloud offers self-hosted online file storage services. Files stored on Nextcloud server can be shared among multiple users with different levels of access permissions. Nextcloud is being used in banking and financial organizations to control business needs. It enables customers and bank employees collaborate by make their data available anywhere through efficient file sharing workflows while keeping customer intelligence in-house.

## Essential Data Flows: Use Cases & Misuse Cases

### 1. View or Access Customer Profiles

### Use Case

When an existing customer visits bank, Bank Teller needs to access the customer profile. In order to view profile, bank teller needs to login. The first task is to enter the address of the Nextcloud server to connect. Then, he needs to enter the login id and the password. 

### Misuse Case

Rogue Teller wants to gain unauthorized access to the server to steal sensitive customer information. He could use, brute-force attack, session hijacking, dictionary attack to gain access to the server. 

### Security Requirements

This attacks can be prevented by implementing progressive delays, invalidating session after logout and by enforcing strong password requirements. However, strong passwords are still vulnerable to keylogger attacks. To prevent this, multi-factor authentication can be used.

### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Misuse%20case%201.jpg)

### 2. Create and Share Links

### Use Case

Bank Teller receives an information request regarding the details of rate of interest on personal loan from a client. In this case, the bank teller creates and shares the link of file which contains detailed information on rate of interest. The client can then use the link to view the information from anywhere.  

### Misuse Case

Rogue Client who is hired by rival bank, wants to gain unauthorized access to steal confidential information related to bank’s credit policy stored on the server. He tries to modify links to gain access to the other confidential information.  

### Security Requirements

Unauthorized access via shared links can be prevented by encrypting links and protecting traffic with Transport Layer Security. 


### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/misuse%20case%202.png)

### 3. Access data from third-party clients

### Use Case

Consider the scenario, where the bank teller requests client to provide proof of property documents in order to sanction loan. Client can then request bank teller that he is away from home and he can share copy of proof of documents stored in his dropbox. Bank Teller can use Nextcloud’s Mount External Storage feature. This feature provides a checkbox which when enabled allows clients in bank’s server share their external storage. Bank Teller can enable this feature and let client know that he can share the required documents through dropbox. Client can then share his document folder in dropbox directly through Nextcloud. 

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/usecase3_example.JPG)

### Misuse case

Rogue Client wants to compromise data on the bank’s server. He can deliberately request bank teller that he wants to share his documents through third party applications. When he gets the permission to share his external storage files, he can create deceptive identity by spoofing internet address. He can spoof internet address by faking the header information on Internet packets to make it look like it came from dropbox. Once he gains access, he can then use this as launching point for further unauthorized access.

### Security Requirements

To prevent this, DDP tools can be used and background configuration checks must also be done.

### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/misuse%20case%203.png)


### 4. Send Customer Log Records

### Use case

Consider a joint account with multiple owners. A client who is an owner of the joint account can request bank employee for log of all owners activity for the last 6 month period. Bank employee can share the activity log of the account to the client. Client can then view all logs related to transaction summary. 

### Misuse case

Rogue teller wants to expose or overwrite sensitive information. He wants to tamper the log records to hide the illegal activity of the co-owner of join account whom he colluded with.

### Security Requirements

Security Requirements
To prevent log tampering, certain immutable attributes can be included which can track every change in the log files.

### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/misuse%20case%204.jpg)

## Alignment of security requirements with advertised features

### Misuse case one:

- Next cloud provides two-factor authentication.
- Next cloud does not offer any progressive delays during login this may be vulnerable to a brute force attack by the hacker.
- Next cloud offers a strong password policy by checking the password against the list of breached passwords from haveibeenpwnd.com. This check creates a hash of the password and sends the first five characters of this hash to the haveibeenpwnd.com API to retrieve a list of all hashes that start with them. Then it checks on the Nextcloud instance if the password hash is in the result set.

### Misuse case two:

- Next cloud implements SAML and Kerberos to provide strong authentication  for client server communication.

### Misuse case three:

- Nextcloud uses plain and simple HTTP traffic for all file handling.
- It does not protect against a hacked device or server, but prevents data transfers on insecure networks like public WiFi networks, mobile devices or third party networks from being intercepted.

## Security-related configuration and installation issues.

### Security related misconfigurations

- While sharing public links to files, users have the ability to use the public link instead of actually logging in into the application. A workaround provided for this is to deny access to all users that are not member of a group.

- Admins should disable external storage option, so that users who have access to external storage cannot change files in the file system. 

### Installation Issues

Normal installation does plain HTTP but there is an ability to use SSL to encrypt server traffic and to protect users login and data in transit. If the server is to be publicly accessible, users should get a certificate signed by a commercial signing authority. All this is required because NextCloud runs on an Apache Server.


