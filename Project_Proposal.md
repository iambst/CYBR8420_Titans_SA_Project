---
# CYBR8420 Project Proposal
---
# Team Name 
```
Titans
```
# Team Members 

Charitha Karnam (ckarnam@unomaha.edu), Lakshmi Prasanna Kaspa(lkaspa@unomaha.edu), Sai Tarun Battula(sbattula@unomaha.edu)

# Project: 
---
Nextcloud Server 
---

Github Link: [Nextcloudserver](https://github.com/nextcloud/server)

# License

All contributions to NextCloud repository from June, 16 2016 on are considered to be licensed under the AGPLv3 or any later version.

# Repository Activity
```
Total Commits:45,558 commits
Branches:115 branches
Total releases : 431 releases
Contributors: 551
```


# Programming Languages usage breakdown:

  - PHP : 57%
  - JavaScript : 40%
  - CSS : 1%
  - Others : 2%
---
# Motivation:

Our selection of the project was based on the common skill set our group members shared (JAVASCRIPT, PHP). Since Nextcloud is about hosting and maintaining user data, security is a major concern in this application. Hence, it would provide us a good platform in learning about software security vulnerabilities.

# Description:
---
Nextcloud is a suite of client-server software for creating and using file hosting services. It is functionally similar to Dropbox, although Nextcloud is free and open-source, allowing anyone to install and operate it on a private server.
In contrast to proprietary services like Dropbox, the open architecture allows adding functionality to the server in the form of applications and enables users to have full control of their data.
  
# Features!
---

  - Nextcloud users can manage calendars (CalDAV), contacts (CardDAV), scheduled tasks and streaming media (Ampache) from within the platform.
  - Content can be shared by defining granular read/write permissions between users and/or groups.
  - Nextcloud users can create public URLs when sharing files. Logging of file-related actions, as well as disallowing access based on file access rules is also available.
  - Users can interact with the browser-based text editor, bookmarking service, URL shortening suite, gallery, RSS feed reader and document viewer tools from within Nextcloud.

# Some security needs
---
  - Secured and confidential submission of client files.
  - Secure the server from Man-in-the-middle attacks.
  - Restrict the access of data by administrators.
  - Proper Encryption algorithms to encrypt the user data in case of unauthorized access.
  - Proper security measures to monitor backup and restore systems.

# Security related history

 **A missing sanitization of search results for an autocomplete field could lead to a stored XSS requiring user-interaction**
        
        This missing sanitization only affected group names, hence malicious search results could only be crafted by privileged users like admins or group admins.


**Improper checks of dropped permissions**

    Nextcloud Server before 12.0.8 and 13.0.3 suffers from improper checks of dropped permissions for incoming shares allowing a user to still request previews for files it should not have access to.

**Improper authentication**

    Nextcloud Server before 12.0.8 and 13.0.3 suffer from improper authentication on the OAuth2 token endpoint. Missing checks potentially allowed handing out new tokens in case the OAuth2 client was partly compromised.

**Breach of Privacy**
    
    
    Nextcloud Server before 10.0.4 and 11.0.2 are vulnerable to disclosure of calendar and address book names to other logged-in users. Note that no actual content of the calendar and address book has been disclosed.
    
**XSS vulnerabilities**
    
    
    Nextcloud Server before 9.0.58 and 10.0.5 and 11.0.3 are vulnerable to an inadequate escaping of error messages leading to XSS vulnerabilities in multiple components.



