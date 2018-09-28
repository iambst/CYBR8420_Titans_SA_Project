# Requirements for Software Security Engineering

## Backstory

Nextcloud offers self-hosted online file storage services. Files stored on Nextcloud server can be shared among multiple users with different levels of access permissions. Nextcloud is being used in banking and financial organizations to control business needs. It enables customers and bank employees collaborate by make their data available anywhere through efficient file sharing workflows while keeping customer intelligence in-house.

## Essential Data Flows: Use Cases & Misuse Cases

### 1. View or Access Customer Profiles

### Use Case

When an existing customer visits bank, Bank Teller needs to access the customer profile. In order to view profile, bank teller needs to login. The first task is to enter the address of the Nextcloud server to connect. Then, he needs to enter the login id and the password. 

### Misuse Case

Rogue Teller wants to gain unauthorized access to the server to steal customer information. He could use, brute-force attack, session hijacking, dictionary attack to gain access to the server. This attacks can be prevented by implementing progressive delays, invalidating session after logout and by enforcing strong password requirements respectively. However, strong passwords are still vulnerable to keylogger attacks. To prevent this, multi-factor authentication can be used.

### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Misuse%20case%201.jpg)

### 2. Create and Share Links

### Use Case

Bank Teller receives an information request regarding the details of rate of interest on personal loan from a client. In this case, the bank teller creates and shares the link of file which contains detailed information on rate of interest. The client can then use the link to view the information from anywhere.  

### Misuse Case

Rogue Client wants to gain unauthorized access to steal confidential information related to bank’s policies stored on the server. He tries to modify links to gain access to the other confidential information.  This can be prevented by encrypting links and protecting traffic with Transport Layer Security. 

### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/misuse%20case%202.png)


