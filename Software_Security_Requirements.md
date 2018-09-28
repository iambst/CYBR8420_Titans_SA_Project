# Requirements for Software Security Engineering

## Backstory

Nextcloud offers self-hosted online file storage services. Files stored on Nextcloud server can be shared among multiple users with different levels of access permissions. Nextcloud is being used in banking and financial organizations to control business needs. It enables customers and bank employees collaborate by make their data available anywhere through efficient file sharing workflows.

## Essential Data Flows: Use Cases & Misuse Cases

## 1. View or Access Customer Profiles

### Use Case

When an existing customer visits bank, Bank Teller needs to access the customer profile. In order to view profile, bank teller needs to login. The first task is to enter the address of the Nextcloud server to connect. Then, he needs to enter the login id and the password. 

### Misuse Case

Rogue Teller wants to gain unauthorized access to the server to steal customer information. He could use, brute-force attack, session hijacking, dictionary attack to gain access to the server. This attacks can be prevented by implementing progressive delays, invalidating session after logout and by enforcing strong password requirements respectively. However, strong passwords are still vulnerable to keylogger attacks. To prevent this, multi-factor authentication can be used.

### UML Diagram

![alt text](https://github.com/iambst/CYBR8420_Titans_SA_Project/blob/master/Misuse%20case%201.jpg)
