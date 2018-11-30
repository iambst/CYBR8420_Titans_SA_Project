
# Code Analysis
## Code Review Strategy:
Our Code Review Strategy is based on checklist based code review strategy to analyze the nextcloud code for any defects that may lead to critical security issues. While reviewing the code, we considered the areas where security plays a major role. Our main focus is on the below entities.
Oauth
Encryption
Files_external
Files_sharing
Twofactor-backupcodes
#### Oauth: 
OAuth (Open Authorization) is an open standard for token-based authentication and authorization on the Internet. It allows an end user's account information to be used by third-party services, such as Facebook, without exposing the user's password.
#### Encryption:
The data is encrypted both on storage and on data transfer.
#### Files_external:
External Files are accessed by Nextcloud server
#### Files_sharing :
Files from third party entities are shared by Nextcloud server.
#### Twofactor-backupcodes:
Nextcloud provides two factor authentication and an in built bruteforce mechanism.<br/>
We also analyzed code based on our Threat model and misuse cases identified.
